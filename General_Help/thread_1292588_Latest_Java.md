---
title: "Latest Java"
date: 2009-10-16
forum: General Help
---

### Post by quietbear on 2009-10-16
I installed the latest Java from the Package Manager (6-16).

However when I go to the java site to test my version, it says I am still with like 1.16 or something, same when I do > about: plugins.

How do I enable the latest version of Java in firefox?

Lamens terms please, I am a beginner.

---

### Post by diafanos on 2009-10-16
Open a terminal and run the following command:

```

sudo update-alternatives --config java

```

then follow the wizard to set your preferred java version


You can find a more detailed guide here:

**[[COLOR="DarkRed"]https://help.ubuntu.com/community/Java[/COLOR]]("https://help.ubuntu.com/community/Java")**

---

### Post by quietbear on 2009-10-16
That sets it for the system, but not which version Firefox is using...

I did that, and am using the most up to date, but Firefox is still using the old version.

---

### Post by Mighty_Joe on 2009-10-16
What is the output from:
```

ls -l /usr/lib/mozilla/plugins
```

There should be a symlink from there to the java plugin.

---

### Post by quietbear on 2009-10-16
> ls -l /usr/lib/mozilla/plugins
total 0
lrwxrwxrwx 1 root root 37 2009-09-25 22:29 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root 43 2009-09-25 19:00 libtotem-cone-plugin.so -> ../../totem/default/libtotem-cone-plugin.so
lrwxrwxrwx 1 root root 42 2009-09-25 19:00 libtotem-gmp-plugin.so -> ../../totem/default/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root 44 2009-09-25 19:00 libtotem-mully-plugin.so -> ../../totem/default/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root 50 2009-09-25 19:00 libtotem-narrowspace-plugin.so -> ../../totem/default/libtotem-narrowspace-plugin.so


There is the output, I have no idea what it is that you said or how to make one.

---

### Post by Mighty_Joe on 2009-10-16
A symlink is like a shortcut in Windows, only Unix systems think they're real files.  Very useful and flexible.
You can see there's no Java in that folder, so the Java plugin is not installed.  You can try to install the plugin package:
```
sudo apt-get install sun-java6-plugin
```
If that doesn't work, you can create the symlink for Firefox to find the plugin like so:
```

cd /usr/lib/firefox/plugins
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.16/jre/plugin/i386/ns7/libjavaplugin_oji.so
```

---

### Post by quietbear on 2009-10-16
Did both, and still no dice:

> ls -l /usr/lib/mozilla/plugins
total 0
lrwxrwxrwx 1 root root 37 2009-09-25 22:29 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root 39 2009-10-16 10:50 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 root root 43 2009-09-25 19:00 libtotem-cone-plugin.so -> ../../totem/default/libtotem-cone-plugin.so
lrwxrwxrwx 1 root root 42 2009-09-25 19:00 libtotem-gmp-plugin.so -> ../../totem/default/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root 44 2009-09-25 19:00 libtotem-mully-plugin.so -> ../../totem/default/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root 50 2009-09-25 19:00 libtotem-narrowspace-plugin.so -> ../../totem/default/libtotem-narrowspace-plugin.so


I know it says I have Java, its the old version, I need the new version that I have now downloaded half a dozen times, and still cant get firefox to use.

---

### Post by Mighty_Joe on 2009-10-16
> **quietbear said:**
> Did both, and still no dice:


It looks like the Java Plugin (or at least the symlink) is installed correctly now.  Did you restart Firefox before checking the plugin?  What does [this site]("http://java.com/en/download/installed.jsp?detect=jre&try=1") say?

---

### Post by quietbear on 2009-10-16
> Your Java version is 1.6.0_0. Please click the button below to get the recommended Java for your computer.

NOTE: If you recently completed your Java software installation, you may need to restart your browser (close all browser windows and re-open) before verifying your installation.
Download Free Java for Linux

Version 6 Update 16 

I have restarted at least half a dozen times, twice the entire computer.

---

### Post by Mighty_Joe on 2009-10-16
What does:
```
sudo update-java-alternatives -l
```
say?  Note that the symlink to the firefox plugin points to /etc/alternatives/mozilla-javaplugin.so, so that program is controlling which version of Java Firefox uses.
Which Firefox version are you using?

---

### Post by quietbear on 2009-10-16
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.14) Gecko/2009090216 Ubuntu/9.04 (jaunty) Firefox/3.0.14

> java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun


---

### Post by donato roque on 2009-10-16
It looks like you have the openjdk version of java.  I know this because I use it instead of the proprietary sun-java version.  If you downloaded both versions, you should choose just one.

---

### Post by quietbear on 2009-10-17
I dont care which version it is as long as one of them is working.

When it was jsut the open source one, Firefox was still using the old version (1.16 or something), and I want it to use the latest, version 6 something.

I have to to get the comments on YouTube to appear right, so I tried to install it, turns out I had it all along and FireFox still doesnt use it all along.

So how do I get Firefox to actually USE the new version rather than the old?

---

### Post by dj-toonz on 2009-10-17
this is what I'm using for java 

Java(TM) Plug-in 1.6.0_16

    File name: libnpjp2.so
    The next generation Java plug-in for Mozilla browsers.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java™ Plug-in 		Yes
application/x-java-applet 	Java™ Plug-in Applet 		Yes
application/x-java-applet;version=1.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.1.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.1.2 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.1.3 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.2 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.2.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.2.2 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.3 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.3.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.4 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.4.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.4.2 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.5 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.6 	Java™ Plug-in 		Yes
application/x-java-applet;jpi-version=1.6.0_16 	Java™ Plug-in 		Yes
application/x-java-bean 	Java™ Plug-in JavaBeans 		Yes
application/x-java-bean;version=1.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.1.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.1.2 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.1.3 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.2 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.2.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.2.2 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.3 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.3.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.4 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.4.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.4.2 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.5 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.6 	Java™ Plug-in 		Yes
application/x-java-bean;jpi-version=1.6.0_16 	Java™ Plug-in


It look's like your using the openJDK java version & that is the latest version in the repo's of openJDK what you've got installed. the 1.6.0_16 is sun java (have you got that installed?

---

