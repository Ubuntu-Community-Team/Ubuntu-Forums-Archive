---
title: "Fatal Java Error"
date: 2011-07-26
forum: General Help
---

### Post by Schalde on 2011-07-26
When i'm running bWin poker in the browser, it won't start and it gives me this error:

```
net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: Could not initialize applet.
    at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:728)
    at net.sourceforge.jnlp.Launcher.getApplet(Launcher.java:672)
    at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:884)
Caused by: net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: A fatal error occurred while trying to verify jars.
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:441)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:169)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:288)
    at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:697)
    ... 2 more
Caused by: 
net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: A fatal error occurred while trying to verify jars.
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:441)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:169)
    at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:288)
    at net.sourceforge.jnlp.Launcher.createApplet(Launcher.java:697)
    at net.sourceforge.jnlp.Launcher.getApplet(Launcher.java:672)
    at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:884)

```How can i solve this problem?

---

### Post by Gyokuro on 2011-07-26
Hi, 

do you use openjdk or Oracle's (Sun) jre? What shows java -version

---

### Post by Schalde on 2011-07-26
Well, i'm kinda newbie in the linux universe. I am pretty sure that it is openjdk.

This error has only occured while running 11.04, when i ran 10.04 there were no problems

---

### Post by Schalde on 2011-07-26
I actually think that i have both installed. Openjdk was installed as a standard. When it gave me the error, i then installed java from java.com but i still got the same problem!

---

### Post by cap10Ibraim on 2011-07-26
i think only one of them is set to default 
I used to have problems with java applets and openjdk , but my applets worked using oracle's java . 
I uninstalled openjdk the follow oracle guide on their website on how to install the java addon on firefox

---

### Post by Gyokuro on 2011-07-26
there is no need to uninstall openjdk as you can choose which one should be used as default:

sudo update-alternatives --config java

or I found a complete guide for Ubuntu: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by cap10Ibraim on 2011-07-26
but for the browser plugin he need to uninstsall icetea... plugin if he want to install oracle's plugin

---

