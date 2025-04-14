pipeline {
  agent any
  tools { 
        maven 'Maven_3_2_5'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=asgbuggywebapp -Dsonar.organization=asgbuggywebapp -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=2fa7b8d1-1ebb-4bd7-a8dd-77a1b88aa35f'
			}
    }

	stage('RunSCAAnalysisUsingSnyk') {
            steps {		
				withCredentials([string(credentialsId: '2fa7b8d1-1ebb-4bd7-a8dd-77a1b88aa35f', variable: '2fa7b8d1-1ebb-4bd7-a8dd-77a1b88aa35f')]) {
					sh 'mvn snyk:test -fn'
				}
			}
    }		
  }
}
