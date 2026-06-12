---
title: "Apache ANT problem"
date: 2011-04-14
forum: General Help
---

### Post by Urema on 2011-04-14
I know this is more of an Apache ANT problem, though I am still running Ubuntu 10.04.

I have set up a simple HelloWeb java web application, I am now trying to run my build.xml with ANT.....however I run into errors.

```

<?xml version="1.0"?>  
<project name="hello" default="deploy_local" basedir=".">  

<property file="build.properties"/> 
  
<path id="classpath">  
	<fileset dir="${lib.dir}" includes="servlet-api.jar"/>  
</path>  
   
<target name="clean">  
	<echo>Cleaning the ${build.dir}</echo>  
	<delete dir="${build.dir}"/>  
	<delete dir="${dist.dir}"/>  
</target>  
   
<target name="init" depends="clean">  
	<echo>Creating the build directory</echo>  
	<mkdir dir="${build.dir}/WEB-INF/classes"/>  
	<mkdir dir="${build.dir}/WEB-INF/lib"/> 
	<mkdir dir="${dist.dir}"/> 
	<mkdir dir="${lib.dir}"/>
</target>  
   
<target name="compile" depends="init">  
	<echo>Compile the source files</echo>  
	<javac srcdir="${src.dir}" destdir="${build.dir}/WEB-INF/classes">  
		<classpath refid="classpath"/>  
	</javac>  
</target>  
  
<target name="copy" depends="compile">  
	<copy todir="${build.dir}/WEB-INF">
		<fileset dir="${web.dir}/WEB-INF"/>  
	</copy>  
	<copy todir="${build.dir}">  
		<fileset dir="${web.dir}"/>  
	</copy>  
	<copy todir="${build.dir}/WEB-INF/lib">  
		<fileset dir="${lib.dir}">  
			<exclude name="servlet-api.jar"/>  
		</fileset>  
	</copy>  
</target>  
  
<target name="war" depends="copy">  
	<echo>Building the war file</echo>  
	<war destfile="${dist.dir}/${project.name}.war" webxml="${build.dir}/WEB-INF/web.xml">  
		<fileset dir="${build.dir}"/>  
	</war>  
</target>  

<target name="deploy_local" depends="war">  
	<echo>Deploying .war to local Tomcat</echo>  
	<copy todir="${tomcat.dir}">  
		<fileset dir="${dist.dir}">  
			<include name="${project.name}.war"/>  
		</fileset>  
	</copy>  
</target>  

</project> 

```

This is my build.xml file

And this is my build.properties

```

project.name=HelloWorldTest
lib.dir=lib  
src.dir="/direct/link/to/src"
web.dir=web  
build.dir=build
dist.dir=dist  
tomcat.dir=/Library/Tomcat/webapps

```

I got an errorsaying that the src.dir directory doesnt exist, and the general view of the public was to point directly to this folder....I done that and the src.dir is found but now the error shifts to the lib.dir etc. THe error log tells me that 'lib' is not found, so I created it and it continues to tell me that 'lib' is not found.

Has anyone ran this simple example, and know how to get around this ANT problem?

Thanks greatly in advance,
U.

---

