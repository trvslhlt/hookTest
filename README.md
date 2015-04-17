##README
###Setup
1. Install the Parse command line tools.
2. Save this shell code as "setup.sh" in the directory where you want the project to live.

	```sh
	#!/bin/sh

	#setup parse environment
	parse new

	#clean up the boilerplate
	cd parse
	rm -rf cloud
	rm -rf public

	#pull in source and setup version control
	git init
	git remote add origin https://bitbucket.org/latchMaster/latch_parse
	git fetch
	git checkout -t origin/rebuild

	#remove sample hook
	rm ./.git/hooks/pre-push.sample

	#add custom hook
	cp ./scripts/pre-push ./.git/hooks/
	```
3. Open Terminal and navigate to the directory containing "setup.sh"
4. Run the shell script. You should be prompted to enter your email and password (for your Latch Parse account).

	```sh
	User$ sh setup.sh
	```

###Usage
When you push local commits to github the Parse cloud code will be redeployed. If the deployment fails the push will not be performed. 
* If you would like to push without deploying you can add the "--no-verify" flag. Like this...

	```sh
	User$ git push --no-verify
	```
