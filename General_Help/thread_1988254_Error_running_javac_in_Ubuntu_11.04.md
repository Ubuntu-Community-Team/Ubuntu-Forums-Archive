---
title: "Error running javac in Ubuntu 11.04"
date: 2012-05-27
forum: General Help
---

### Post by sahrkhanaki on 2012-05-27
I'm trying to install JDK 1.7 in Ubuntu 11.04 but when I run the following command:
  ```
javac -version
```  I'm getting error below:
  ```
Error: could not find libjava.so
Error: Could not find Java SE Runtime Environment.
```  here is some information about my system configuration for you in order to solve my problem:
  The end of /etc/profile:
  ```
JDK_HOME=/usr/local/java/jdk1.7.0_04
PATH=$PATH:$HOME/bin:$JDK_HOME/bin
JAVA_HOME=/usr/local/java/jre1.7.0_04
PATH=$PATH:$HOME/bin:$JAVA_HOME/bin
export JDK_HOME
export JAVA_HOME
export PATH
```  output of /etc/ld.conf.so.d/java.conf :
  ```
/usr/local/java/jre1.7.0_04/lib/i386/
/usr/local/java/jre1.7.0_04/lib/i386/jli/
```  output of $PATH:
  ```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/sahar/bin:/usr/local/java/jdk1.7.0_04/bin:/home/sahar/bin:/usr/local/java/jre1.7.0_04/bin
```  Please help me to solve my problem.

---

### Post by maverickaddicted on 2012-05-29
Check This

[http://www.linuxquestions.org/questions/slackware-14/system-not-finding-libjava-so-765259/](http://www.linuxquestions.org/questions/slackware-14/system-not-finding-libjava-so-765259/)

---

