---
title: "Tomcat 7 and 12.04"
date: 2012-08-04
forum: General Help
---

### Post by wiggumon on 2012-08-04
Hello,

I am pretty new to Linux and I have been trying to setup Tomcat. I used the instructions here:

[http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/](http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/)

and changed them to fit Tomcat 7. I have edited my .bashrc file with the following:

export JAVA_HOME=/usr/bin/java

Now this did work once but when I rebooted and go to localhost:8080 after running ./startup.sh the Tomcat startup page does not appear. This is the output from ./startup.sh:

Using CATALINA_BASE:   /usr/local/tomcat
Using CATALINA_HOME:   /usr/local/tomcat
Using CATALINA_TMPDIR: /usr/local/tomcat/temp
Using JRE_HOME:        /usr/bin/java
Using CLASSPATH:       /usr/local/tomcat/bin/bootstrap.jar:/usr/local/tomcat/bin/tomcat-juli.jar

And this is the output from running ./shutdown.sh:

Using CATALINA_BASE:   /usr/local/tomcat
Using CATALINA_HOME:   /usr/local/tomcat
Using CATALINA_TMPDIR: /usr/local/tomcat/temp
Using JRE_HOME:        /usr/bin/java
Using CLASSPATH:       /usr/local/tomcat/bin/bootstrap.jar:/usr/local/tomcat/bin/tomcat-juli.jar
./catalina.sh: 1: eval: /usr/bin/java/bin/java: not found

I am not sure what I am doing wrong. When I do a which java I get the following: /usr/local/tomcat/bin$. Can anyone point me in the right direction? I'm not trying to auto start Tomcat or anything complicated but I just can't seem to get this to run after editing .bashrc and rebooting.

Thanks!

---

### Post by wiggumon on 2012-08-04
Never mind. I edited the bash.bashrc file and setup my JAVA_HOME.

---

