pipeline {
  agent any
  stages {
    stage('BuildStage') {
      steps {
        git(url: 'https://github.com/pnmayur9/rbrepo', branch: 'master', credentialsId: 'fdb59003-f017-436c-91df-9ab2a0baf79b')
        sh '''sudo docker build -t pnmayur/rbrepo:latest .
sudo docker push pnmayur/rbrepo:latest'''
      }
    }

    stage('DeployDev') {
      parallel {
        stage('DeployDev') {
          steps {
            sh '''sudo docker build -t pnmayur/rbrepo3:latest .
sudo docker push pnmayur/rbrepo3:latest'''
          }
        }

        stage('DeployQA') {
          steps {
            echo 'Deployed'
          }
        }

      }
    }

  }
}