---
title: "Tomca5 setup"
date: 2006-06-03
forum: General Help
---

### Post by noeluylee on 2006-06-03
Hi, I just had my tomcat5 working after a day of configuration. after installation, when I start my tomcat like this /etc/init.d/tomcat5 start  i encounter rhis message

Could not start Tomcat 5 servlet engine because no Java Development Kit
(JDK) was found. Please download and install JDK 1.3 or higher and set
JAVA_HOME in /etc/default/tomcat5 to the JDK's installation directory.

So I set my java_home like this.  
export JAVA_HOME="/usr/lib/jvm/java-1.5.0-sun-1.5.0.06"
export PATH=$PATH:$JAVA_HOME/bin

Then, the tomcat runs when i sudo /etc/init.d/tomcat5 start, and was able to login on the tomcat administrator, however, when I tried to add new host, I encounter error page, something like page cannot be found, so I decided to do /etc/init.d/tomcat5 stop then /etc/init.d/tomcat5 start, however, again I enounter this error:

Could not start Tomcat 5 servlet engine because no Java Development Kit
(JDK) was found. Please download and install JDK 1.3 or higher and set
JAVA_HOME in /etc/default/tomcat5 to the JDK's installation directory.

Everytime I do /etc/init.d/tomcat5 start, I encounter that error, it seems that it doesnt save my configuration.

When I run this command on konsole "which java" it says /usr/bin/java

When I tried to use /usr/bin/java on java_home it just doesnt work.

Hope you guys could help me out here :)

Thanks a lot :)

---

### Post by noeluylee on 2006-06-04
Any help!?  :confused:

---

### Post by mlind on 2006-06-04
define JAVA_HOME on */etc/enviromment*
then it's global for everyone on your setup. No need to export it there I guess.

Or export it on your ~/.bashrc

---

### Post by killernurd on 2006-07-07
Check your config file to see if it's actually remembering the changes.

Also, try putting this into /etc/profile

```

export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.06

```

That *should* make it the default for all users, including root and any user that is created for a specific server (such as Tomcat).

At least, that worked for me :)

Also, for Tomcat, you might have to specify the path for CATALINA_HOME, so if you need to, find where that is and put it into /etc/profile:

```

export CATALINA_HOME=<path/to/your/catalina/engine/home>

```

Of course, anything in ~/.bashrc will override that on a per-user basis, if you need it to, and export should always work from the command line.

---

### Post by hldub on 2006-07-09
Hi,

Using apt-get I too found that I needed to export JAVA_HOME to get tomcat to work. I had a hard time figuring it out aswell (perhpas I'm not too smart). Having installed and used ant with apt-get without $JAVA_HOME I didn't expect to have to do anything to get tomcat to work. 

Isn't it the debian way not to have to do this? Should tomcat depend on jdk or something?

No expert,

hldub

---

