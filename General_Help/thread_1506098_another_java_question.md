---
title: "another java question"
date: 2010-06-10
forum: General Help
---

### Post by meomike2000 on 2010-06-10
ok, here is my situation, i have downloaded and installed java.
works well, can write and compile classes and even get them to run via
```
java className
```

followed this how-to for tomcat:
> [http://ubuntuforums.org/showthread.php?p=226828](http://ubuntuforums.org/showthread.php?p=226828)
and it works have compiled some simple servlets and can view them via localhost....

here is the problem, in my /.bashrc file i had to add these lines via the above how-to before i could compile my servlets or i will get errors that the javax.servlet packages dont exist...

lines i added to /.bashrc
```

export JAVA_HOME=/usr/lib/jvm/java-6-openjdk
export CLASSPATH=/usr/local/tomcat/common/lib/jsp-api.jar:/usr/local/tomcat/com$

```

but now when i try to compile or run a none servlet java class i get errors, if i dont have them enabled i can not compile servlets....

is there a fix for this or do i just have to enable/disable to do one or the other...

reason this is a problem is some of the stuff i am trying to do requires both servlets and normal java files and makes for a lot of logout and in to compile a program...

i am new to java so i am prob doing something wrong, please help if u can....

thanks in advance mike

---

### Post by LiquidMeson on 2010-06-10
adding the locations and stuff you have to do in windows, but shouldn't have to do in linux when java is installed properly. 

I believe the packages in the repository should work for compiling/ running java apps. Open up System>Admin>Synaptic and install all the java stuff you think you need. Remove all the other stuff you had before.

Note: stuff in the linux world moves alot faster then windows,..so you might need to google for a guide more up-to-date, say 2010, rather then 2005

---

### Post by meomike2000 on 2010-06-10
i can compile and run java apps, i just can not compile and run java apps and compile java servlets at the same time, have to commenting out the line:

> 
export CLASSPATH=/usr/local/tomcat/common/lib/jsp-api.jar:/usr/local/tomcat/common/lib/servlet-api.jar


to run java apps, have to enable to compile java servlets.....

when this line is commented out i can run java apps, when it isnt i can not...

when this line is commented out i can not compile java servlets......

i need to do both at once.......

both works just not at same time......

thanks mike....

---

### Post by LiquidMeson on 2010-06-10
pulled this [http://www.coreservlets.com/Apache-Tomcat-Tutorial/tomcat6.0-files/autoexec-sample.bat.txt](http://www.coreservlets.com/Apache-Tomcat-Tutorial/tomcat6.0-files/autoexec-sample.bat.txt)

maybe tailor you bash file to look more like that? (different dirs of course)

ref:[http://www.coreservlets.com/Apache-Tomcat-Tutorial/development-environment.html#Java-Home](http://www.coreservlets.com/Apache-Tomcat-Tutorial/development-environment.html#Java-Home)

---

### Post by meomike2000 on 2010-06-10
this looks to lean towards a windows setup, my setup is on a ubuntu 9.10...

will work with this tomorrow night, time for bed, thanks for the help....

---

### Post by meomike2000 on 2010-06-10
well i think that i found a way to solve my problem, seams to work anyhow, can now compile a servlet and can also run a java app...

i made this (exert from my /.bashrc file):
> export CLASSPATH=/usr/local/tomcat/common/lib/jsp-api.jar:/usr/local/tomcat/common/lib/servlet-api.jar

look like this:
> export CLASSPATH=$CLASSPATH:/usr/local/tomcat/common/lib/jsp-api.jar:/usr/local/tomcat/common/lib/servlet-api.jar

like i said, problem seams to be solved.....

hope this may help others, mike

---

