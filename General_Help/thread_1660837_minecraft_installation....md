---
title: "minecraft installation?..."
date: 2011-01-05
forum: General Help
---

### Post by mbrown9412 on 2011-01-05
OK, i'm attempting to run minecraft. on minecraft.net, it says i can download mincraft.jar, and run it, and if i run into out of memory errors to launch it with this: java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame

however, I soon found out I didn't have Sun JVM. so I went over to their website, and downloaded the.bin file - how do I install it?

I also tried installing cacao, which sadly, wasn't much help either. i could tell ubuntu to run Minecraft.jar with it, however, nothing happened.


what should I do?

---

### Post by hawkmage on 2011-01-05
The Sun Java JRE in is not installed by default.  To install it you will you will need to have the partner repository added to apt-get.  

First backup the existing repository file:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```Source the distro info to set environment variables run:
```
. /etc/lsb-release
```You need the leading period to have the variables set in your current session.

Next add the repositories to the file:
```
if [ ! "`grep "ubuntu ${DISTRIB_CODENAME} partner" /etc/apt/sources.list`" ]
then
    echo 'deb http://archive.canonical.com/ubuntu ${DISTRIB_CODENAME} partner' >> /etc/apt/sources.list
    echo 'deb-src http://archive.canonical.com/ubuntu ${DISTRIB_CODENAME} partner' >> /etc/apt/sources.list
fi
```Update the apt-get cache:
```
sudo apt-get update
```Install Sun Java:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```Set the Sun Java as the default:
```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by waspbloke on 2011-01-06
I am having the same problem I guess...

SunJVM is installed but when I run Minecraft, after the login prompt the window just turns black.

Any ideas?

---

### Post by mcduck on 2011-01-06
> **waspbloke said:**
> I am having the same problem I guess...

SunJVM is installed but when I run Minecraft, after the login prompt the window just turns black.

Any ideas?

Have you set the Sun JVM as the default for Java applications?

```
sudo update-alternatives --config java
```

---

### Post by mcduck on 2011-01-06
> **hawkmage said:**
> The Sun Java JRE in is not installed by default.  To install it you will you will need to have the partner repository added to apt-get.  

First backup the existing repository file:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```Source the distro info to set environment variables run:
```
. /etc/lsb-release
```You need the leading period to have the variables set in your current session.

Next add the repositories to the file:
```
if [ ! "`grep "ubuntu ${DISTRIB_CODENAME} partner" /etc/apt/sources.list`" ]
then
    echo 'deb http://archive.canonical.com/ubuntu ${DISTRIB_CODENAME} partner' >> /etc/apt/sources.list
    echo 'deb-src http://archive.canonical.com/ubuntu ${DISTRIB_CODENAME} partner' >> /etc/apt/sources.list
fi
```Update the apt-get cache:
```
sudo apt-get update
```Install Sun Java:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```Set the Sun Java as the default:
```
sudo update-java-alternatives -s java-6-sun
```

...or just place a single checkmark in Software Sources to enable the Partners repository, install Sun JWM with your choice of package management tool, and then run the update-alternatives command to set it as default. ;)

---

### Post by hawkmage on 2011-01-06
> **mcduck said:**
> ...or just place a single checkmark in Software Sources to enable the Partners repository, install Sun JWM with your choice of package management tool, and then run the update-alternatives command to set it as default. ;)
It was not listed for me in the software sources so I had to add it.  Also I a number of systems I have are esentially headless that I manage through the console or ssh and can't rely on the GUI.

---

### Post by mcduck on 2011-01-06
> **hawkmage said:**
> It was not listed for me in the software sources so I had to add it.  Also I a number of systems I have are esentially headless that I manage through the console or ssh and can't rely on the GUI.
Well, if a person is trying to get Minecraft running he probably is running a GUI, so GUI instructions are appropriate.

Also the Partner repository should be on the Other Software-tab of the Software Sources by default. Of course if you've done a minimal/server install things might be different, but once again that's rather unlikely setup considering what the thread is about... ;)

---

### Post by waspbloke on 2011-01-06
> **mcduck said:**
> Have you set the Sun JVM as the default for Java applications?

```
sudo update-alternatives --config java
```

Yes. It gives me 3 options with Sun set as default.

I even tried running it on my VBox winXP guest but then it throws an error that it can't find an OpenGL device - I have Vbox guest additions and 3D enabled, this supposedly confers OpenGL support to the guest OS.

This is bugging me. I have paid for this game after playing on a friends machine but for me, no combination of OS/Java seems to want to get it working.


EDIT:

Seems to be OpenGL reated, I get this when I run from the console (after login):

```

	at net.minecraft.client.Minecraft.a(SourceFile:231)
	at net.minecraft.client.Minecraft.run(SourceFile:641)
	at java.lang.Thread.run(Thread.java:662)
Caused by: java.lang.ArrayIndexOutOfBoundsException: 0
	at org.lwjgl.opengl.XRandR$Screen.<init>(XRandR.java:234)
	at org.lwjgl.opengl.XRandR$Screen.<init>(XRandR.java:196)
	at org.lwjgl.opengl.XRandR.populate(XRandR.java:87)
	at org.lwjgl.opengl.XRandR.access$100(XRandR.java:52)
	at org.lwjgl.opengl.XRandR$1.run(XRandR.java:110)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.lwjgl.opengl.XRandR.getConfiguration(XRandR.java:108)
	at org.lwjgl.opengl.LinuxDisplay.init(LinuxDisplay.java:618)
	at org.lwjgl.opengl.Display.<clinit>(Display.java:135)

```

I'm guessing this is due to the finicky bloody ATI drivers - which are installed and compiz has all the lovely effects - so what else is there?

---

### Post by hawkmage on 2011-01-06
> **mcduck said:**
> Well, if a person is trying to get Minecraft running he probably is running a GUI, so GUI instructions are appropriate.

Also the Partner repository should be on the Other Software-tab of the Software Sources by default. Of course if you've done a minimal/server install things might be different, but once again that's rather unlikely setup considering what the thread is about... ;)
I guess I am a bit old school on things like this.  I prefer the command line to do my system administration/configuration.  Also I figured that I would give a solution that would work in most situations.

It adds the correct Partner repository for the current Ubuntu distro if needed, installs the Sun Java 6 jre and makes it the default.  It will work on any version of Ubuntu that there is Sun Java 6 jre package in the Partners repository.

---

### Post by mbrown9412 on 2011-01-06
which partner box should i check?

I have partner, and then one with source code


secondly, what package manager would you suggest i use for jvm, as it is a .bin


I wouldn't know, as i just run ubuntu as a secondary os, instead of the version of xp my school gives me : )

---

### Post by mbrown9412 on 2011-01-06
okay I did the coding way

it installed java, however, when i told it to be default this is what i got: ```
max@max-laptop:~$ sudo update-java-alternatives -s java-6-sun
update-alternatives: error: no alternatives for appletviewer.
update-alternatives: error: no alternatives for apt.
update-alternatives: error: no alternatives for extcheck.
update-alternatives: error: no alternatives for HtmlConverter.
update-alternatives: error: no alternatives for idlj.
update-alternatives: error: no alternatives for jar.
update-alternatives: error: no alternatives for jarsigner.
update-alternatives: error: no alternatives for javac.
update-alternatives: error: no alternatives for javadoc.
update-alternatives: error: no alternatives for javah.
update-alternatives: error: no alternatives for javap.
update-alternatives: error: no alternatives for java-rmi.cgi.
update-alternatives: error: no alternatives for jconsole.
update-alternatives: error: no alternatives for jdb.
update-alternatives: error: no alternatives for jhat.
update-alternatives: error: no alternatives for jinfo.
update-alternatives: error: no alternatives for jmap.
update-alternatives: error: no alternatives for jps.
update-alternatives: error: no alternatives for jrunscript.
update-alternatives: error: no alternatives for jsadebugd.
update-alternatives: error: no alternatives for jstack.
update-alternatives: error: no alternatives for jstat.
update-alternatives: error: no alternatives for jstatd.
update-alternatives: error: no alternatives for native2ascii.
update-alternatives: error: no alternatives for rmic.
update-alternatives: error: no alternatives for schemagen.
update-alternatives: error: no alternatives for serialver.
update-alternatives: error: no alternatives for wsgen.
update-alternatives: error: no alternatives for wsimport.
update-alternatives: error: no alternatives for xjc.
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/apt
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/HtmlConverter
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jar
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javac
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javadoc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javah
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/java-rmi.cgi
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jconsole
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jdb
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jhat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jinfo
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jmap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jps
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jrunscript
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jsadebugd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstack
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstatd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/schemagen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/serialver
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsgen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsimport
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/xjc


```

is this correct, seeing as how it says everything does not exist?


anyway, it did install correctly, however when I right click on Minecraft.jar, and say to use java to run it, this pops up in a window:

```
he file '/home/max/Desktop/Minecraft.jar' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.
```




what does this mean?

---

### Post by r00t4rd3d on 2011-01-06
Once you get java installed along with the java browser plugin :

[www.minecraft.net/play.jsp]("www.minecraft.net/play.jsp")

ftw !

---

### Post by mbrown9412 on 2011-01-06
Good idea, but I won't have wifi all the time - plus, if i feel like playing at my school, I can't access the internet there while using ubuntu, they have it hidden and locked with a very strong password (trust me, i've tried, successfully getting tech angry with me)

---

### Post by MaxIBoy on 2011-01-07
Go to the package manager and install the package "sun-java6-plugin."

Then run the game with this command:
```
/usr/lib/jvm/java-6-sun-1.6.0.22/bin/java -Dsun.java2d.opengl=true -jar /path/to/Minecraft.jar
```
The 1.6.0.22 part might be different on your system, just run the command
```
ls /usr/lib/jvm/java-6-sun*
``` to see what it is.

---

### Post by mcduck on 2011-01-07
> **hawkmage said:**
> I guess I am a bit old school on things like this.  I prefer the command line to do my system administration/configuration.  Also I figured that I would give a solution that would work in most situations.

It adds the correct Partner repository for the current Ubuntu distro if needed, installs the Sun Java 6 jre and makes it the default.  It will work on any version of Ubuntu that there is Sun Java 6 jre package in the Partners repository.

Yep, so do I. :D

But when helping other people I try to give them the easiest possible instructions, which isn't always the same as what I'd do myself. :)

---

### Post by mcduck on 2011-01-07
> **mbrown9412 said:**
> okay I did the coding way

it installed java, however, when i told it to be default this is what i got: ```
max@max-laptop:~$ sudo update-java-alternatives -s java-6-sun
update-alternatives: error: no alternatives for appletviewer.
update-alternatives: error: no alternatives for apt.
update-alternatives: error: no alternatives for extcheck.
update-alternatives: error: no alternatives for HtmlConverter.
update-alternatives: error: no alternatives for idlj.
update-alternatives: error: no alternatives for jar.
update-alternatives: error: no alternatives for jarsigner.
update-alternatives: error: no alternatives for javac.
update-alternatives: error: no alternatives for javadoc.
update-alternatives: error: no alternatives for javah.
update-alternatives: error: no alternatives for javap.
update-alternatives: error: no alternatives for java-rmi.cgi.
update-alternatives: error: no alternatives for jconsole.
update-alternatives: error: no alternatives for jdb.
update-alternatives: error: no alternatives for jhat.
update-alternatives: error: no alternatives for jinfo.
update-alternatives: error: no alternatives for jmap.
update-alternatives: error: no alternatives for jps.
update-alternatives: error: no alternatives for jrunscript.
update-alternatives: error: no alternatives for jsadebugd.
update-alternatives: error: no alternatives for jstack.
update-alternatives: error: no alternatives for jstat.
update-alternatives: error: no alternatives for jstatd.
update-alternatives: error: no alternatives for native2ascii.
update-alternatives: error: no alternatives for rmic.
update-alternatives: error: no alternatives for schemagen.
update-alternatives: error: no alternatives for serialver.
update-alternatives: error: no alternatives for wsgen.
update-alternatives: error: no alternatives for wsimport.
update-alternatives: error: no alternatives for xjc.
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/apt
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/HtmlConverter
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jar
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javac
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javadoc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javah
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/java-rmi.cgi
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jconsole
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jdb
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jhat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jinfo
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jmap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jps
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jrunscript
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jsadebugd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstack
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstatd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/schemagen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/serialver
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsgen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsimport
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/xjc


```

is this correct, seeing as how it says everything does not exist?


anyway, it did install correctly, however when I right click on Minecraft.jar, and say to use java to run it, this pops up in a window:

```
he file '/home/max/Desktop/Minecraft.jar' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.
```




what does this mean?
The errors are fine, it's just telling that you only have one program/package that provides such features, and therefore no need to select between any alternatives.

What comes to the executable error, you need to set the executable permission on the minecraft.jar:

```
chmod +x /home/max/Desktop/Minecraft.jar
```

..or right-click the file, select Properties and on the Permissions-tab mark the "Allow executing file as program"-checkbox.

---

