
https://www.youtube.com/watch?v=89yWXXIOisk&list=PLhW3qG5bs-L_ZCOA4zNPSoGbnVQ-rp_dG - Just Ok.
https://www.youtube.com/watch?v=Un5JEX1Bxq4 - Better.

>>>How to checkin the project to GitHub
GitHub Commands
Login to GitHub Repository and create new Repo
--suraless@gmail.com/Github@1984

--Install Git
--Goto GitBash or command prompt
-- git init(from the location which you wants to commit to). This will create .git at this location
--git status(to check new files)
--git add . ->Add to git
--git commit -m "comit message"
Adding to remote repository.
--Create new Repo in GIT(Ex -MyNewRepo).
git remote add origin https://github.com/suraless/MyNewRepo.git =>Create remote repo
git push  -u origin master

That's all about how to commit to GitHub


>>>****Compile and package the applicatio from command prompt*****
1.Goto cmd pom.xml
2.mvn compile
3.mvn package
*****


>>>build and package the Git hosted Maven project from Jenkins.
>>>>HOW TO BUILD<<<<
1.Create new item - FreeStyle
2.Under source code management Select Git and mention the repo path (https://github.com/suraless/Repo3)
3.Dont mention any credentials as your repo is public. Mention otherwise.
4.Under build ->
	In Add build steps select "Ïnvoke Top-Level Maven Build" and in Goal enter as "compile"
5.In Advance enter the application name under pom (Ex - in my case I entered UserApplication. If it doesnt work try to enter /UserApplication/Pom.xml ....do some R&D if it fails)
Do build and check for the console output.
6. Jenkins workspace location is C:\Program Files (x86)\Jenkins\workspace\jenkins_maven\
	Basically, Jenkins downloads from the Repo and creates a new project under Jenkins_maven folder. And then issues a mvn pom command on it to do a build
	
	After build is done, then there are multiple PostBuild actions - Trigger email, Archive Build War files, Clean Build
	If you want to do build after every chekin - use Poll SCM functionality where it will keep polling from the SCM
	
>>>>HOW TO DEPLOY<<<<
Dont do above two steps of build and packaging.
Under Post-build actions ->Select deploy war/ear to container.
Provide War/ear files - **/sample.war
context path - sample.war
Add Tomcat 7 and provide the user id/pwd. Create new credentials admin/admin in your tomcat/user-config.xml. Mention it here and from dropdown then select
Save and build now.

>>>>HOW TO BUILD+PACKAGE+DEPLOY<<<<
This needs piping. Piping is chaining of various events together.