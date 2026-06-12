---
title: "Eclipse runs fine from command line, but not launcher?"
date: 2005-03-02
forum: General Help
---

### Post by blueturtle on 2005-03-02
Hi guys, quick question for you there.

Running eclipse from the command line is fine, e.g.
# /usr/local/eclipse/eclipse

but creating a after creating a launcher for
/usr/local/eclipse/eclipse , it complains that it can't find the Java Runtime Environment (JRE). 

Any thoughts?

Cheers,
Neil

---

### Post by bryan986 on 2005-03-17
Well, on a positivie note, I was able to get eclipse running finally because of this, I was trying to run the binary and getting that error, and now I tried through the command line and it works like a charm, heh...

I tried adding the java install to the path variable, but I could not get it to launch by doubleclicking on the binary without getting that error

---

### Post by bored2k on 2005-03-17
[QUOTE=bryan986]Well, on a positivie note, I was able to get eclipse running finally because of this, I was tring to run the binary and getting that error, and now I tried through the command line and it works like a charm, thanks!

I tried adding stuff to the path variable, but I could not get it to launch by doubleclicking on the binary without getting that error[/QUOTE]
 What is Eclipse ?

---

### Post by bryan986 on 2005-03-17
Its a programing environment for many languages like java,php,python etc

[http://www.eclipse.org](http://www.eclipse.org)

---

### Post by Scirious on 2005-03-28
This a solutiona I made to be able to create a launcher for Eclipse in Gnome. Part of this solution was created with information provided from [http://ubuntuguide.org](http://ubuntuguide.org).

Well, both my Java and Eclipse ware installed in /opt.

Java is in /opt/java/jdk1.5.0_02 (I'm using jdk 1.5)
Eclipse is in /opt/eclipse

First, create a file called launcher.sh in eclipse's folder.

Add the following to this file

JAVA_HOME=/opt/java/jdk1.5.1_02
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH
cd /opt/eclipse
./eclipse

Than, add this script as the command to be executed for your icon on the desktop.

Hope it helps.
Scirious.

---

### Post by KLineD on 2005-03-28
[QUOTE=Scirious]This a solutiona I made to be able to create a launcher for Eclipse in Gnome. Part of this solution was created with information provided from [http://ubuntuguide.org](http://ubuntuguide.org).

Well, both my Java and Eclipse ware installed in /opt.

Java is in /opt/java/jdk1.5.0_02 (I'm using jdk 1.5)
Eclipse is in /opt/eclipse

First, create a file called launcher.sh in eclipse's folder.

Add the following to this file

JAVA_HOME=/opt/java/jdk1.5.1_02
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH
cd /opt/eclipse
./eclipse

Than, add this script as the command to be executed for your icon on the desktop.

Hope it helps.
Scirious.[/QUOTE]
That's exactly how I did it and it works.

---

