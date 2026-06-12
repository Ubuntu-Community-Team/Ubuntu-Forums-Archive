---
title: "Trouble installing Intellij ......"
date: 2010-10-22
forum: General Help
---

### Post by whitetimer on 2010-10-22
Hi All 

Right i am trying to install Intellij on Xubuntu 10:10 and i get this error 


No JDK found to run IDEA. Please validate either IDEA_JDK or JDK_HOME points to valid JDK installation
exec: 67: /bin/java: not found

This is my bashrc environment settings 

## JAVA_HOME ##
export JAVA_HOME=/usr/lib/jvm/jdk1.6.0_21
export PATH=$PATH:$JAVA_HOME/bin

## JDK_HOME ##
export JDK_HOME=/usr/lib/jvm/jdk1.6.0_21
export PATH=$PATH:$JDK_HOME/bin

## IDEA_JDK ##
export IDEA_JDK=/usr/lib/jvm/jdk1.6.0_21
export PATH=$PATH:$IDEA_JDK/bin

export JRE_HOME=/usr/lib/jvm/jdk1.6.0_21/jre
export PATH=$PATH:$JRE_HOME/bin

Any suggestions please ???

Many thanks :(

---

### Post by lykeion on 2010-10-22
Assuming you have the correct path to JDK_HOME it should work with these settings if you launch the idea launcher script <intellij_install_folder>/bin/idea.sh in a terminal.

However I find it's easier to set the path in the idea launcher script directly. Just open <intellij_install_folder>/bin/idea.sh and add this in the beginning:
export JDK_HOME=<your_jdk_path>

---

