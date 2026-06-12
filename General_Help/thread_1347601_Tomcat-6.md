---
title: "Tomcat-6"
date: 2009-12-06
forum: General Help
---

### Post by karthi_slm on 2009-12-06
hai,

 I installed tomcat6 in my system I configured my environmental variable (java_home,Path,classpath,jre_home).I started my tomcat using "sudo" command in the terminal. It goes well but when I shutdown the tomcat 
I am getting this error

Using CATALINA_BASE:   /usr/share/tomcat6
Using CATALINA_HOME:   /usr/share/tomcat6
Using CATALINA_TMPDIR: /usr/share/tomcat6/temp
Using JRE_HOME:       /usr
6 Dec, 2009 10:13:46 PM org.apache.catalina.startup.Catalina stopServer
SEVERE: Catalina.stop: 
java.io.FileNotFoundException: /usr/share/tomcat6/conf/server.xml (No such file or directory)
    at java.io.FileInputStream.open(Native Method)
    at java.io.FileInputStream.<init>(FileInputStream.jav  a:137)
    at org.apache.catalina.startup.Catalina.stopServer(Ca  talina.java:407)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Nativ  e Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(Native  MethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(De  legatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.apache.catalina.startup.Bootstrap.stopServer(B  ootstrap.java:337)
    at org.apache.catalina.startup.Bootstrap.main(Bootstr  ap.java:415)

Any help would be appreciated............

---

### Post by KingWilliam on 2009-12-06
If I look at your error:

```
java.io.FileNotFoundException: /usr/share/tomcat6/conf/server.xml
```

I think you are missing some setup files. Try looking for that file, if it is missing (like the error is telling you), you might want to google for an example server.xml file.

---

### Post by karthi_slm on 2009-12-06
Hai [KingWilliam]("http://ubuntuforums.org/member.php?u=419831")

U are correct , but my srver.xml file resides into /usr/share/tomcat6/skel/conf/server.xml.
I am unable to reloacate the folder. Tell me how to change the location of the file.

Thanks

---

### Post by karthi_slm on 2009-12-06
[FONT=Courier New]hai [/FONT][KingWilliam]("http://ubuntuforums.org/member.php?u=419831")
I used the follwing command to stop and start the tomcat It works...
[FONT=Courier New]$ sudo /etc/init.d/tomcat6 stop
   Stopping Tomcat servlet engine tomcat6                                                                          [ OK ] 
$ sudo /etc/init.d/tomcat6 start
   Starting Tomcat servlet engine tomcat6                                                                          [ OK ]
Thanks for your help......
[/FONT]

---

### Post by edojan on 2009-12-07
Hi, I am having a similar issue with Tomcat6. It appears that the startup.sh is assuming that CATALINA_BASE and CATALINA_HOME (preset at:   /usr/share/tomcat6) contain /conf/server.xml which is in reality is located at /usr/share/tomcat6/skel/conf

In my case it also tries to find /usr/share/tomcat6/temp directory which is not there. 

 I wonder how to fix this? Here is the log

Dec 7, 2009 12:14:04 AM org.apache.catalina.startup.Embedded initDirs
SEVERE: Cannot find specified temporary folder at /usr/share/tomcat6/temp
Dec 7, 2009 12:14:04 AM org.apache.catalina.startup.Catalina load
WARNING: Can't load server.xml from /usr/share/tomcat6/conf/server.xml
Dec 7, 2009 12:14:04 AM org.apache.catalina.startup.Embedded initDirs
SEVERE: Cannot find specified temporary folder at /usr/share/tomcat6/temp
Dec 7, 2009 12:14:04 AM org.apache.catalina.startup.Catalina load
WARNING: Can't load server.xml from /usr/share/tomcat6/conf/server.xml
Dec 7, 2009 12:14:04 AM org.apache.catalina.startup.Catalina start
INFO: Server startup in 0 ms
java.lang.reflect.InvocationTargetException
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)

---

### Post by KingWilliam on 2009-12-07
In that case, I can not help you. I do remember that it is hard to set up tomcat in ubuntu, IF you take it from the repos. My recommendation is to download the latest tomcat version from their official site and untar/zip it in a directory on your system. This way always worked for me.

Good luck.

---

### Post by DavidBooth on 2011-10-03
I got it working!   I had also been having trouble getting tomcat6 to start after installation via Synaptic Package Manager, running on Ubuntu 10.04.  When trying to start tomcat6 via /usr/share/tomcat6/bin/startup.sh I was getting this error:
[FONT=Courier New]
  Using CATALINA_BASE:   /usr/share/tomcat6
  Using CATALINA_HOME:   /usr/share/tomcat6
  Using CATALINA_TMPDIR: /usr/share/tomcat6/temp
  Using JRE_HOME:        /usr
  Using CLASSPATH:       /usr/share/tomcat6/bin/bootstrap.jar
  touch: cannot touch `/usr/share/tomcat6/logs/catalina.out': No such file or directory
  ./catalina.sh: 452: cannot create /usr/share/tomcat6/logs/catalina.out: Directory nonexistent[/FONT]

I tried manually creating the /usr/share/tomcat6/logs directory, but that did not help, as I then found this error in the log file /usr/share/tomcat6/logs/catalina.out :

[FONT=Courier New]  WARNING: Can't load server.xml from /usr/share/tomcat6/conf/server.xml[/FONT]

In other words, tomcat6 was not finding server.xml .  Another post in this thread (thanks!)  finally helped me figure out that CATALINA_BASE must be set to /var/lib/tomcat6  rather than letting it default to /usr/share/tomcat6 or setting it to /etc/tomcat6, even though /var/lib/tomcat6/conf is a symbolic link to /etc/tomcat6 .   In my case I also had to change port numbers in server.xml to avoid conflict with other servers I was already running, but others may not need to do that.  Finally, I also created a missing temp directory to avoid this error in the log file /var/lib/tomcat6/logs/catalina.out , though I do not know whether I really needed to do so:

[FONT=Courier New]  SEVERE: Cannot find specified temporary folder at /var/lib/tomcat6/temp[/FONT]

To be clear, **here are the steps I used to get tomcat6 working:**

1. You need to start tomcat6 as root and edit server.xml as root,
so start a root shell and the remaining steps will be done under root:

[FONT=Courier New]  $ sudo bash
  Password: [/FONT]
  
2. Tell tomcat6 where to find server.xml and other config files:

[FONT=Courier New]  # export CATALINA_BASE=/var/lib/tomcat6[/FONT]
  
3. (If needed) edit server.xml to change port numbers from the defaults:

[FONT=Courier New]  # cd /var/lib/tomcat6
  # cp -p server.xml server.xml.old
  # vi server.xml
  [ . . . ]
  [/FONT]
4. Create a temp directory (while running as root) and set
the permissions the same as those I see for the logs directory.   I do NOT know
whether this step was necessary or advisable, but it did get
rid of the warning message:

[FONT=Courier New]  # ls -ld /var/lib/tomcat6/logs/
  drwxr-x--- 2 tomcat6 adm 4096 2011-10-03 09:57 /var/lib/tomcat6/logs/
  # mkdir /var/lib/tomcat6/temp
  # chown tomcat6 /var/lib/tomcat6/temp
  # chgrp adm /var/lib/tomcat6/temp[/FONT]

5. Remove the old log file and start tomcat:

[FONT=Courier New]  # rm /var/lib/tomcat6/logs/catalina.out
  # cd /usr/share/tomcat6/bin/
  # ./startup.sh
  Using CATALINA_BASE:   /var/lib/tomcat6
  Using CATALINA_HOME:   /usr/share/tomcat6
  Using CATALINA_TMPDIR: /var/lib/tomcat6/temp
  Using JRE_HOME:        /usr
  Using CLASSPATH:       /usr/share/tomcat6/bin/bootstrap.jar
  #[/FONT]

6. Check the log file for errors:

[FONT=Courier New]  # cat /var/lib/tomcat6/logs/catalina.out 
  Oct 3, 2011 2:40:03 PM org.apache.catalina.core.AprLifecycleListener init
  INFO: The APR based Apache Tomcat Native library which allows optimal performance in production environments was not found on the java.library.path: /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/server:/usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.26/jre/../lib/i386:/usr/java/packages/lib/i386:/lib:/usr/lib
  Oct 3, 2011 2:40:03 PM org.apache.coyote.http11.Http11Protocol init
  INFO: Initializing Coyote HTTP/1.1 on http-18080
  Oct 3, 2011 2:40:03 PM org.apache.catalina.startup.Catalina load
  INFO: Initialization processed in 490 ms
  Oct 3, 2011 2:40:03 PM org.apache.catalina.core.StandardService start
  INFO: Starting service Catalina
  Oct 3, 2011 2:40:03 PM org.apache.catalina.core.StandardEngine start
  INFO: Starting Servlet Engine: Apache Tomcat/6.0.24
  Oct 3, 2011 2:40:03 PM org.apache.catalina.startup.HostConfig deployDescriptor
  INFO: Deploying configuration descriptor ROOT.xml
  Oct 3, 2011 2:40:03 PM org.apache.catalina.startup.HostConfig deployDescriptor
  INFO: Deploying configuration descriptor host-manager.xml
  Oct 3, 2011 2:40:03 PM org.apache.catalina.startup.HostConfig deployDescriptor
  INFO: Deploying configuration descriptor manager.xml
  Oct 3, 2011 2:40:03 PM org.apache.catalina.startup.HostConfig deployDescriptor
  INFO: Deploying configuration descriptor docs.xml
  Oct 3, 2011 2:40:03 PM org.apache.catalina.startup.HostConfig deployDescriptor
  INFO: Deploying configuration descriptor examples.xml
  Oct 3, 2011 2:40:04 PM org.apache.coyote.http11.Http11Protocol start
  INFO: Starting Coyote HTTP/1.1 on http-18080
  Oct 3, 2011 2:40:04 PM org.apache.catalina.startup.Catalina start
  INFO: Server startup in 579 ms
  #[/FONT]

7.  Looks good! Now test from a browser by browsing to [http://localhost:8080/](http://localhost:8080/) .  You should get a page that says "It works !".

---

### Post by Clay Ferguson on 2013-03-01
DavidBooth, thanks for your post. It helped me get tomcat up on Rackspace Ubuntu server. 

this line was the important one:
export CATALINA_BASE=/var/lib/tomcat6

and also I had to manually create the 'logs' folder under /usr/share/tomcat7.

When you do the basic 'apt-get install tomcat7' to install (instead of downloading a zip file), those are the two steps you have to do to get it up and running it appears.

---

