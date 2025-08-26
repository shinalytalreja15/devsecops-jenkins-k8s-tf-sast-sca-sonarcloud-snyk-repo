pipeline {
  agent any
  tools { 
        maven '_3.8.4'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=shinalytalreja15 -Dsonar.organization=shinalytalreja15 -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=618089842f30843bc69a66e3775bc069b377e15d'
			}
        } 

	stage('RunSCAAnalysisUsingSnyk') {
            steps {		
				withCredentials([string(credentialsId: 'shinalytalreja15', variable: 'shinalytalreja15')]) {
					sh 'mvn snyk:test -fn'
				}
			}
    }		
  }
}
