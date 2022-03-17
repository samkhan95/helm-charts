
pipeline{
    agent any
    stages{
        stage(setting up cluter){
            steps{
                sh 'minikube delete'
                sh 'minikube start --driver=docker --cpus=5'
            }    
            
        }
     
        stage("Deploy the app to kubernetes cluster"){
            steps{
                
                sh 'helm install aegis-front ./aegis-front'
                sh 'helm install aegis-back ./aegis-back'
                sh 'helm install db ./db'
            }
        }

        stage("for the PR"){
            when{
                branch 'PR-*'
            }
            
            steps {
                echo "this only runs for PRs"
            }
        }
    }
}
