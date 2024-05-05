pipeline {
	agent {
	    label 'Windows_Node'
	}
	stages {
		stage ('Git-Checkout') {
			steps{
				echo "Checking out from git repo";
				git branch: 'main', url: 'https://github.com/simple3r/jenkingsScrip.git'
			}
		}
		
		stage('Build'){
			steps {
				echo "Building the git project";
				bat 'Build.bat'
			}
		}
		
		stage('unit-test'){
			steps {
				echo "Junit Done";
				bat 'Unit.bat'
			}
			
		}
		
		stage('QA'){
			steps {
				echo "Sonar Done";
				bat 'Quality.bat'
			}
		}
		
		stage('Deploy'){
			steps{
				echo "Pass!";
				bat 'Deploy.bat'
			}
		}	
	}

	post {
		always {
			echo 'This will always run';
		}
		success {
			echo 'This will run only if successful';
		}
		failure {
			echo 'This will run only if failed';
		}
		unstable {
			echo 'This will run only if unstable';
		}
		changed { // Se corrigió el nombre de la etapa
			echo 'This will run only if the state of the PL has changed';
			echo 'For example, if the PL was previously failing but is now successful';
		}
	}
}
