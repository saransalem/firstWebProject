pipeline {
    agent any
  tools {
          maven "MAVEN_HOME"
    }
    stages {
        stage('Build') {
            steps {
                echo 'Build App'
		    bat 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                echo 'Test App'
		    bat 'mvn test'
            }
        }
        stage('Package') {
            steps {
                echo 'Package App'
		    bat 'mvn package'
            }
        }
	    
	    
        stage('Artifacts') {
            steps {
                echo 'Artifacts App'
		archiveArtifacts artifacts: '**/target/*.jar', followSymlinks: false
            }
        }
	    
        stage('Deploy') {
            steps {
                echo 'Deploy App'
              deploy adapters: [tomcat9(credentialsId: 'aa4319dc-2133-442c-862c-5ca1585a174f', path: '', url: 'http://192.168.29.108:8080/')], contextPath: null, war: '**/*.war'
		    }
        }
		
		}
		post
		{
			failure
			{
				emailext body: 'Your pipeline script aborted !!', subject: 'Pipeline script is failed', to: 'saransalem30@gmail.com'			
			}
			always
			{
				emailext body: 'Your pipeline script aborted !!', subject: 'Pipeline script is failed', to: 'saransalem30@gmail.com'			
			}
		}
}
