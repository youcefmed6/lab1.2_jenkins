pipeline{
	agent any
	stages {

		stage("clone the project"){
			steps{
				git "https://github.com/malkiAbdelhamid/lab4_jenkins"
			}
		}

     	stage("Install dependencies "){
			steps{
				bat "npm install"
			}
     	}
		stage("Test"){
			steps{
			 // Run tests and save output to a file
                script {
                // Run the tests and capture the output
                    def testResult = bat(script: "npm test", returnStatus: true)
                    // Check if the tests passed
                    if (testResult != 0) {
                        error("Tests failed!")
                    }
			}
		}
		}

		stage ("Build"){

			steps{
				bat 'npm run build'
			}

		}

		stage("build docker image"){
			steps{
				bat 'docker build -t my-node-app .'
			}
		}
	}
}