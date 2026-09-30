pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool 'SonarScanner'

                    withSonarQubeEnv(
                        installationName: 'SonarQube',
                        credentialsId: 'sonarqube-token'
                    ) {
                        sh """
                            export SONAR_TOKEN="\$SONAR_AUTH_TOKEN"
                            "${scannerHome}/bin/sonar-scanner"
                        """
                    }
                }
            }
        }
    }
}
