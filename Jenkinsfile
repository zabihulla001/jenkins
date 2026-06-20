pipeline{
  agent any
  environment{
    docker = credentials('docker')
  }
  stages{
    stage('clone'){
      steps{
        git branch: 'main',url: 'https://github.com/zabihulla001/jenkins.git'
      }
    }
    stage('docker_build'){
      steps{
        sh 'docker build -t zabihulla01/webapp .'
      }
      }
      stage('login'){
        steps{
          sh 'echo $docker_PSW | docker login -u $docker_USR --password-stdin'
        }
        
      }
    stage('push'){
      steps{
        sh 'docker push zabihulla01/webapp'
      }
    }
    stage('deploy'){
      steps{
        sh 'docker rm -f webapp'
        sh 'docker run -d -p 80:80 zabihulla01/webapp'
      }
    }
  }
}
