pipeline{
    agent any
    stages{
        stage('code') {
            steps {
                git branch: 'main', url: 'https://github.com/shaiksulthanhussainvali/Zomato-Clone.git'
            }
        }
        stage("Build"){
            steps{
                sh "docker build . -t zomato-application"
            }
        }
        stage("Pushing to Docker Hub"){
            steps{
                withCredentials([usernamePassword(credentialsId:"Docker-Hub-Credentials",passwordVariable: 'S.Hussain@123', usernameVariable: 'dockerhussain')]){
                sh "docker tag zomato-application ${env.dockerhussain}/zomato-application:latest"
                sh "docker login -u ${env.dockerhussain} -p ${env."S.Hussain@123"}"
                sh "docker push ${env.dockerhussain}/zomato-application:latest"
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "deploy"
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}
