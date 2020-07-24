pipeline {
  agent any
  environment {
    DEPLOY_CREDS = credentials('anypoint-deployment')
    MULE_VERSION = '4.2.2'
  }
  stages {
    stage('Build') {
      steps {
            bat 'mvn clean -DskipTests package'
      }
    }

    stage('Test') {
      steps {
          bat 'mvn test'
      }
    }

     stage('Deploy Development') {
      environment {
        ENVIRONMENT = 'Sandbox'
      }
      steps {
            bat 'mvn deploy -DmuleDeploy -Dusername="%DEPLOY_CREDS_USR%" -Dpassword="%DEPLOY_CREDS_PSW%" -Denv="%ENVIRONMENT%"'
      }
    }
  }
}