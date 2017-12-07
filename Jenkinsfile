properties([parameters([choice(choices: ['"Integration/n unittesting"'], description: 'Testing environment', name: 'Environment'), booleanParam(defaultValue: false, description: 'Database buiding', name: 'Rebuild Database'), booleanParam(defaultValue: false, description: 'deployingg', name: 'Deploy'), string(defaultValue: 'Default', description: 'Default branch', name: 'Branch')]), pipelineTriggers([])])
node {
 	// Clean workspace before doing anything
    deleteDir()

    try {
        stage ('Clone') {
        	checkout scm
        }
        stage ('Build') {
        	sh "echo 'shell scripts to build project jjj'"
		
        }
        stage ('Tests') {
	        parallel 'static': {
	            sh "echo 'shell scripts to run static tests...'"
	        },
	        'unit': {
	            sh "echo 'shell scripts to run unit tests...'"
	        },
	        'integration': {
	            sh "echo 'shell scripts to run integration tests...'"
	        }
        }
      	stage ('Deploy') {
            sh "echo 'shell scripts to deploy to server...'"
      	}
    } catch (err) {
        currentBuild.result = 'FAILED'
        throw err
    }
}



