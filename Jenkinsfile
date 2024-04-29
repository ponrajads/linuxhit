pipeline{

	agent {label 'linux'}

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/ponrajads/linuxhit.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t ponrajbpr/first-test:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push ponrajbpr/first-test:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
