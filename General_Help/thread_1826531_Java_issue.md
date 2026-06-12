---
title: "Java issue"
date: 2011-08-16
forum: General Help
---

### Post by djdharia on 2011-08-16
[CENTER][LEFT]I get this error when I try to open a java file:
net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: Could not initialize application.
    at net.sourceforge.jnlp.Launcher.createApplication(Launcher.java:776)
    at net.sourceforge.jnlp.Launcher.launchApplication(Launcher.java:552)
    at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:887)
Caused by: net.sourceforge.jnlp.LaunchException: Fatal: Application Error: Cannot grant permissions to unsigned jars.
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.setSecurity(JNLPClassLoader.java:260)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:180)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:294)
    at net.sourceforge.jnlp.Launcher.createApplication(Launcher.java:767)
    ... 2 more
Caused by: 
net.sourceforge.jnlp.LaunchException: Fatal: Application Error: Cannot grant permissions to unsigned jars.
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.setSecurity(JNLPClassLoader.java:260)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:180)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:294)
    at net.sourceforge.jnlp.Launcher.createApplication(Launcher.java:767)
    at net.sourceforge.jnlp.Launcher.launchApplication(Launcher.java:552)
    at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:887)
[LEFT]
[/LEFT]

java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.2) (6b22-1.10.2-0ubuntu1~11.04.1)
OpenJDK Server VM (build 20.0-b11, mixed mode)


I have been trying to figure out how to solve this problem for last day. I am pretty much a noob so any help at this point would be greatly appreciated and thank you in advance.
[/LEFT]
[/CENTER]

---

### Post by ofnuts on 2011-08-16
> **djdharia said:**
> [CENTER][LEFT]I get this error when I try to open a java file:
net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: Could not initialize application.
    at net.sourceforge.jnlp.Launcher.createApplication(Launcher.java:776)
    at net.sourceforge.jnlp.Launcher.launchApplication(Launcher.java:552)
    at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:887)
Caused by: net.sourceforge.jnlp.LaunchException: Fatal: Application Error: Cannot grant permissions to unsigned jars.
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.setSecurity(JNLPClassLoader.java:260)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:180)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:294)
    at net.sourceforge.jnlp.Launcher.createApplication(Launcher.java:767)
    ... 2 more
Caused by: 
net.sourceforge.jnlp.LaunchException: Fatal: Application Error: Cannot grant permissions to unsigned jars.
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.setSecurity(JNLPClassLoader.java:260)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:180)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:294)
    at net.sourceforge.jnlp.Launcher.createApplication(Launcher.java:767)
    at net.sourceforge.jnlp.Launcher.launchApplication(Launcher.java:552)
    at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:887)
[LEFT]
[/LEFT]

java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.2) (6b22-1.10.2-0ubuntu1~11.04.1)
OpenJDK Server VM (build 20.0-b11, mixed mode)


I have been trying to figure out how to solve this problem for last day. I am pretty much a noob so any help at this point would be greatly appreciated and thank you in advance.
[/LEFT]
[/CENTER]
What do you call "open a Java file"? 

A Java source file (.jave) is just a text file and is edited with any text editor. 

Otherwise there is .class and .jar (.jar is really a .zip of .class). You can't really "open" them (well, you can open the .jar like you open a .zip) but to run them you have to call the java runtime which is the "java" command usually (sometimes the "jre" one). So how do you call it?

And where do these files come from?

---

### Post by djdharia on 2011-08-16
the file is called viewer.jnlp and it is from [http://www.pathoma.com/](http://www.pathoma.com/) I am not sure if that helps. Everytime I tried running the file using the IcedTea application, I got the following error that was listed.

---

### Post by ofnuts on 2011-08-17
> **djdharia said:**
> the file is called viewer.jnlp and it is from [http://www.pathoma.com/](http://www.pathoma.com/) I am not sure if that helps. Everytime I tried running the file using the IcedTea application, I got the following error that was listed.A JNLP file si a "Java Web Start" file. In other words this is a  boostrap for a Java app that is pulled & installed before being run on your system. I think you need to have a small "Java Web Start" package already installed on your machine for this to work. See: [http://en.wikipedia.org/wiki/JNLP](http://en.wikipedia.org/wiki/JNLP)

---

### Post by austinap on 2012-06-03
Has anyone come up with a solution to this problem?  I recently subscribed to pathoma as well and am having the same issue and haven't been able to find a work around.  The same jnlp works fine under OS X.  I have icedtea and javaws installed, I don't think that's the issue.

---

### Post by Gyokuro on 2012-06-03
Hi 

As it works on Mac OS (which use sun/oracle java) I think your application is not compatible with openjdk and therefore you should install the JRE from Oracle. Here is a link with a step by step howto [http://www.liberiangeek.net/2012/04/install-oracle-java-jdk-7-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/install-oracle-java-jdk-7-in-ubuntu-12-04-precise-pangolin/)

---

### Post by austinap on 2012-06-03
When I try to run it with the oracle JDK, the splash screen comes up and then closes without anything opening (no warnings, errors, nothing).  Not quite sure what's going on since it does work perfectly well under OS X.  Any ideas?  In any case, thanks for your help.

---

### Post by JimS on 2012-07-09
...
Gyokuro

I will try your suggestion on my
Ubuntu 10.04 LTS on 64bit laptop.

But first I must remove all old Java.
I've started by opening Ubuntu Software Center
and removing Icedtea Java Plugin.
It has been in progress for a long time,
over 60 minutes, so I think something is wrong.
Progress is stopped at 90%.

Any suggestions.

JimS
...

---

### Post by adi-ss on 2012-09-05
I wish to share the error experience I have.

I also have similar problem when run a java program/application (the application is ChartNexus)

The error suddently appear recently (around 1 month ago) (I was use 10.4 Lucid), after I click the application icon (as ussual I do open it), the error message appear.

I was still can run the application by run the Sun/Oracle Java Web start, and run the file / application from its menu.


Now after I upgrade the 10.4 to 12.4,the Java Web Start installed now is IcedTea. Somehow I can not install the Sun/Oracle Java Web start again. 

And the same error come again, when I am off line.
If the system get online to internet, the application can work smoothly just by click the application's icon.

For this moment, I can not run the application from IcedTea web start menu, the menu to run the file is not found.

I am still looking for better way out for this situation.


Regards
Adi Satya

---

