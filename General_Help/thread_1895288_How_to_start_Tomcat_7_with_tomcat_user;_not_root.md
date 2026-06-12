---
title: "How to start Tomcat 7 with tomcat user; not root?"
date: 2011-12-14
forum: General Help
---

### Post by medokr on 2011-12-14
Hello All!

I have a question about setting up Tomcat 7 on ubuntu server. In short, I am unable to start tomcat server using my user (user: tomcat; group: tomcat). I am able to get it started and showing the default welcome page using root.

I would like assistance understanding how to get tomcat server running with the correct user.

Here is some basic information.

**My capabilities:**
I am new to Linux; taken one intro course. I can navigate around ok...I will research commands or switches if I dont understand one you've recommended. I may ask why a specific switch is used in a situation.

**My objective:**
I want to run JSP pages on tomcat 7; and learn to secure the web server.

My goal is to convert over to JSP from visual basic. I've been learning Java, Java Servlets over the past year and half. I've always used tomcat, glassfish embedded in Eclipse and Netbeans. I would like to completely setup tomcat server so i can replicate on a virtual server provided by a web hosting company.

**My computer is running:**
Ubuntu Server, with Linux 2.6.38-13-server x86_64
ubuntu 11.04 server


**Probably too much information:**
- I have installed from CD, no server options selected (ftp, dns, samba, lamp, etc).
- Updated repository: apt-get update
- Upgraded files: apt-get upgrade
- Upgraded Distribution: apt-get dist-upgrade
- Added sysstat, enabled system activity reporting (SAR)
- Added nmap 
- Downloaded and installed openjdk-6-jre and openjdk-6-jdk

_Tomcat Download:_
Retrieved tomcat 7 from apache.hoxt.com
[COLOR=darkred]$wget apache.hoxt.com/tomcat/tomcat-7/v7.023/bin/apache-tomcat-7.023.tar.gz[/COLOR]

_Extracted files and set in permanent location:_
$tar xzvf apache-tomcat-7.0.23.tar.gz
[COLOR=darkred]$sudo mv apache-tomcat-7.0.23 /var/lib/tomcat[/COLOR]

_Set environment variables (I chose in /etc/environment):_
[COLOR=darkred]$sudo vi /etc/environment[/COLOR]
    CATALINA_HOME="/var/lib/tomcat"
    CATALINA_BASE="/var/lib/tomcat"
    JAVA_HOME="/usr/lib/jvm/java-1.6.0-openjdk"

_Created tomcat group & user and changed ownership of Tomcat directory_
[COLOR=darkred]$groupadd tomcat
$useradd -g tomcat -s /sbin/nologin -m -d /home/tomcat tomcat
$passwd tomcat
$chown -R tomcat.tomcat /var/lib/tomcat[/COLOR]

[U]Changed Permissions of tomcat log directory
[/U][COLOR=darkred]$sudo chmod -R 777 /var/lib/tomcat/logs[/COLOR]

_Changed permissions of server.xml_
[COLOR=darkred]sudo chmod A=wx /var/lib/tomcat/conf/server.xml[/COLOR]

**Start up tomcat server. This is where i am stuck...**
Following the instructions [here]("http://www.puschitz.com/InstallingTomcat.html#InstallingTomcatSoftware"), I am trying to start tomcat server using the tomcat user (not root). I am unsuccessful and I am not sure why.

First, I looked at the /Logs/catalina.out log file; which is blank (prior to running the start up script). I attempt to start tomcat server by running the command:

[COLOR=darkred]$su -p -s /bin/sh tomcat $CATALINA_HOME/bin/startup.sh
$_
[/COLOR]
When running this command, there is no output to terminal. I also checked the catalina.out log file and it is still blank. So i do not understand why no response. I thought i would see an error message at terminal output if command or any parameters are wrong.

Now if i run the command below using sudo, it starts up and i see the start up log entries recorded in catalina.out

[COLOR=darkred]$sudo sh startup.sh
Using CATALINA_BASE:  /var/lib/tomcat
Using CATALINA_HOME: /var/lib/tomcat
Using CATALINA_TMPDIR:  /var/lib/tomcat/temp
Using JRE_HOME: /usr
Using CLASSPATH:  /usr/lib/tomcat/bin/bootstrap.jar:/var/lib/tomcat/bin/tomcat-juli.jar[/COLOR]
[COLOR=darkred]$ _[/COLOR]

And tomcat welcome page is working.

**My question again: **Do you have advice on how to use tomcat user to start Tomcat 7 server? 

Thank you for your assistance! Gregg

---

### Post by gordintoronto on 2011-12-14
You have Tomcat 7, and followed instructions for Tomcat 6?

Have a look around here: [http://www.coderanch.com/forums/f-56/Tomcat](http://www.coderanch.com/forums/f-56/Tomcat)

---

### Post by medokr on 2011-12-14
Hi!

Thank you for response. I had been following the tutorial. So far its seems to be basic stuff. Nothing too technically specific such as configuring settings. 

I believe all i have done should be generic. I downloaded tomcat, put into a permanent location, created a user, changed ownership of the Tomcat directory and tried to start it up.

I will look around the link you sent. Thanks!

---

### Post by stylishkoala on 2012-11-13
You probably get best results installing tomcat7 via easyway by ubuntu installer?:
```
sudo apt-get install tomcat7
```

This way tomcat7 start as a service(later you can setting when the service start with update-rc.d), this is what you want or I missunderstand your issue?

---

