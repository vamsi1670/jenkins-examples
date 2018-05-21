# jenkins-examples

Steps required:

1.	Install Jenkins
2.	Install java ,git,maven .
3.	Install tomcat 7.x version in windows. 
a.	In server.xml change the  connector port to 9090.
b.	In the users.xml change include the roles oof tomcat to give the manager access.
 		<role rolename="manager-gui"/>
  		<role rolename="manager-script"/>
  		<user username="admin" password="admin" roles="manager-gui,manager-script"/>

       4.Go to Jenkins dashboard and create a new project.
	In the git url give the source code from git repository.
	In the build step , select windows batch command (windows)
	In the post build action ,select  deploy war/ear to a container.	
			Give the credentials. As given in the tomcat users.xml.
			I have given as admin and admin 
			Tomcat URL as  http://localhost:9090 ( in my case)

Select on build now option and the war file will be deployed to the tomcat server.


SCHEDULEC BUILDS:
1.GO TO MANAGE JENKINS and download schedule  Jenkins plugin.
2.Create a new job enter the required details i.e., pulling git repository or executing commands in windows or shell.
3.com back to main page of Jenkins the you can see the scheduled build option,in which you have to specify the date and time of the build.
4.usually production servers  or any deployment in production would be scheduled using this procedure.
5.After reaching the specified time you can see the build id successful.

HOW to setup delivery pipeline job in Jenkins.:
1.Create 3 jobs named build test and deploy.
2. in the build options give sample commands to be executed.
3.Go to the build triggers option (sample deploy job.) and select the option build after the other projects are built (select the sample build job in the drop down list.)
4.Go to the build test job and in the build triggers option select the buoild after the other projects are built.(Select the Sampledeploy job in the drop down lost.)
5.Install the delivery pipeline plugin 
6.Go to delivery pipeline view in dashboard.
7.Select the + option in the dashboard and select the delivery pipeline. (name it as test delivery pipeline.)
8.Go to the pipelines component option and select the initial job as sample build job.
In this pane you can view all the builds in a chain type , one after the other.
9.Go to edit view of the project and select the Number of pipeline instances per pipeline 
Select the  number as you wish to see all  the no. of the builds in a single page.
In the same edit view select the Enable start of new pipeline build view also. Once you enable this you can see the  BUILD ICON  in the delivery pipeline only which is easy to build the jobs on a go.
10.In the edit view select the enable rebuild option as you can see the individual builds can be rebuilt in the delivery pipeline.
11.seelct the total build time to see the build time of the pipeline build.

How to setup build pipeline in Jenkins.
1.We have already created all the 3 jobs sample build deploy and test jobs and chained thee jobs.
2.install build pipeline plugin.
3.we have to do build pipeline view for this to be done.
We have to go to dashboard and select the + icon and select the build pipeline view.
Go to pipeline flow and in the upstream/downstream config select the sample build job.as initial job.
Select the no of displayed builds to increase the total no. of builds view on the screen.

HOW TO CHANGE THE HOME DIRECTORY OF JENKINS:
Why to  change the home directory is , if this is installed in user profile we have to move to place where we have sufficient disc place.
1.check your home directory.
Go to manage Jenkins -> configure system -> you can see the  home directory where Jenkins is installed.
2.Create a new folder which will be new home directory and go the place where  .jenkins is located and copy all the data (files) to the new folder.
3.change the environment variable JENKINS_HOME and set to new folder.
4.restart Jenkins “Java -jar Jenkins.war.” or restart Jenkins.

How to create users manage users + assign roles:
1.go to manage Jenkins -> manage users -> create users -> create users and assign passwords.
2.configure the users:
     a. go the user on the top right side and select configure, you can canfigure the users.
3. Create and manage the user roles.
     Install roles based strategy plugin. And restart Jenkins.
4.Manage Jenkins -> ensure that enable security is checked. 
5.login as admin and go to configure global security and select the role based strategy.
 After this step try to login as user then you cannot login as user, saying access denied.
6. login as admin -> manage Jenkins -> manage plugins ->role based strategy .
You can see the users, roles and macros in the manage and assign roles option.
	In global roles add a role by name employee.
              In project role add a project by name developer and select all the check boxes in the roles.and patterm dev.* (which means a developer will have access to project which starts with dev.)
              Similarly add tester as another project role and assign all the permissions.
ASSIGN ROLES :
              In the same pane select the assign roles and assign the roles to the user1 and user2 as employee 
              In the project roles  or item roles add user1 and user2 . save and exit.

Testing of the users is valid  or not:
Create 2 new jobs in Jenkins dashboard by name dev.proj and test.proj .
Signout as admin and login as user1 or user2 you will be able to see only the assigned roles to the users respectively.
Basic Configurations in Jenkins.

1.how to change the home directory is already seen.
2.Root directory says all tehbuild information  is stored.
3.root directory : where al the build records are stored on the file system.
4.No. of executors means the no. of parallel jobs that this Jenkins instance is ale to run.
5.labels: this can be better explained by using manage nodes.
Go to manage Jenkins -> manage nodes -> select the new node - >


Writing a POM.XML These are must:

<project>
	<groupId>org.qt</groupId>
	<artifactId>hello-world</artifactId>
	<version>1.0-snapshot</version>
	<packaging> jar </packaging>
	<modelVersion>4.0.0 </modelVersion>
</project>



