---
title: "installing tomcat-7.0.27 by startup.sh shows incorrect JRE_HOME"
date: 2012-09-04
forum: General Help
---

### Post by dragonfly41 on 2012-09-04
When installing apache-tomcat-7.0.27 referring to here ..
[http://diegobenna.blogspot.co.uk/2011/01/install-tomcat-7-in-ubuntu-1010.html](http://diegobenna.blogspot.co.uk/2011/01/install-tomcat-7-in-ubuntu-1010.html)
I've set a number of environment variables in ~/.bashrc

```

export JAVA_HOME=/usr/lib/jvm/java-6-openjdk
export JDK_HOME=/usr/lib/jvm/java-6-openjdk
export JRE_HOME=/usr/lib/jvm/java-6-openjdk/jre [COLOR=Navy][COLOR=Navy][COLOR=Red]<<<< correct path[/COLOR][/COLOR][/COLOR]

export CATALINA_BASE=/usr/local/apache-tomcat-7.0.27
export CATALINA_HOME=/usr/local/apache-tomcat-7.0.27
export CATALINA_TMPDIR=/usr/local/apache-tomcat-7.0.27/temp

export PATH=/usr/local/sbin
export PATH=$PATH:/usr/local/bin
export PATH=$PATH:/usr/sbin
export PATH=$PATH:/usr/bin
export PATH=$PATH:/sbin
export PATH=$PATH:/bin
export PATH=$PATH:/usr/games

#add JAVA variables to default path
export PATH=$PATH:$JAVA_HOME/bin
export PATH=$PATH:$JAVA_HOME/lib

export CLASSPATH=$CATALINA_BASE/bin/bootstrap.jar
export CLASSPATH=$CLASSPATH:$CATALINA_BASE/bin/tomcat-juli.jar

```
after running [COLOR=Navy]sudo source ~/.bashrc[/COLOR]

I can test these environment variables .. without rebooting .. e.g.

[COLOR=Navy]sudo echo $JRE_HOME
/usr/lib/jvm/java-6-openjdk/jre[/COLOR]


Now I can launch tomcat7 by
[COLOR=Navy]sudo /usr/local/apache-tomcat-7.0.27/bin/startup.sh[/COLOR]

and the output on running startup.sh is ..

[COLOR=Navy]Using CATALINA_BASE:   /usr/local/apache-tomcat-7.0.27
Using CATALINA_HOME:   /usr/local/apache-tomcat-7.0.27
Using CATALINA_TMPDIR: /usr/local/apache-tomcat-7.0.27/temp
[COLOR=Navy]Using JRE_HOME:        /usr         [COLOR=Red] <<<< this is an incorrect short path[/COLOR][/COLOR]
Using CLASSPATH:       /usr/local/apache-tomcat-7.0.27/bin/bootstrap.jar:/usr/local/apache-tomcat-7.0.27/bin/tomcat-juli.jar[/COLOR]

Tomcat server launches as localhost:8080 and runs examples o.k..

However .. my question is why on launching startup.sh does JRE_HOME point to 
only /usr

[COLOR=Navy]"Using JRE_HOME:        /usr[/COLOR]"

and not the longer path set in ~/.bashrc above?

[COLOR=Navy]export JRE_HOME=/usr/lib/jvm/java-6-openjdk/jre[/COLOR]

Is this a question for the tomcat forum?

---

### Post by dragonfly41 on 2012-09-04
I soon found the answer here ..

[http://ubuntuforums.org/showthread.php?t=977956](http://ubuntuforums.org/showthread.php?t=977956)

Apparently I should be launching startup.sh with [COLOR=Navy]sudo **-E** flag[/COLOR] since root resets $JRE_HOME to tomcat default (/usr).

[COLOR=Navy]sudo **-E**  /usr/local/apache-tomcat-7.0.27/bin/startup.sh

[/COLOR]that solves the problem  .. full path to JRE_HOME is now seen.

---

