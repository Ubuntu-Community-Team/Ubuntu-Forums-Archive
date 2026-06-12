---
title: "Google Chrome+Ubuntu+Java"
date: 2009-09-01
forum: General Help
---

### Post by alligoodw on 2009-09-01
I already have flash up and running with Google Chrome (not chromium) for Ubuntu.  Now I need to know how I get it to run Java. Anyone know how?

---

### Post by paradigm2 on 2009-09-01
I don't know and haven't researched it but I think you mean Chromium, right?

---

### Post by NoaHall on 2009-09-01
No. Chromium (open source) is what is built on, Chrome is the "real deal" (closed source) from Google.

As for java, tried enabling plug ins by force?

---

### Post by alligoodw on 2009-09-01
I have the real deal from Google.

---

### Post by NoaHall on 2009-09-01
Hehe, "real deal".

Any luck with java? It works fine for me, using the 64 bit version. I just installed under a different browser, and chrome picked it up.

---

### Post by alligoodw on 2009-09-01
> **NoaHall said:**
> Hehe, "real deal".

Any luck with java? It works fine for me, using the 64 bit version. I just installed under a different browser, and chrome picked it up.

I could be wrong though!  I picked up my .deb Google Chrome file from here:  [http://fileforum.betanews.com/detail/Google-Chrome-for-Linux/1220379960/3](http://fileforum.betanews.com/detail/Google-Chrome-for-Linux/1220379960/3)

Maybe I've had too much coffee to drink this evening. :D  At any rate, do I need to reinstall the javaplugin again?

---

### Post by paradigm2 on 2009-09-01
> **alligoodw said:**
> I have the real deal from Google.

I consider chromium more the real deal because it's a pure open source project but I guess to each their own.  Almost the same thing.

---

### Post by NoaHall on 2009-09-01
Yeah, the version you have is the Chrome, not the open source version.
I'd reinstall Java, maybe through another browser or something. (then use sudo ldconfig, might help some things)

---

### Post by Rebootkid on 2009-12-09
sudo apt-get install sun-java6-plugin

got me working

Oh, and you've got to add --enable-plugins to the menu item that starts Chrome.

---

### Post by Freiberg on 2010-03-28
> **Rebootkid said:**
> sudo apt-get install sun-java6-plugin



I tried that, but I got "E: Couldn't find package 'sun-java6-plugin'."  Anything else I could try?

---

### Post by hotpocket1234 on 2010-04-05
i tryied it and it worked fine

---

### Post by Russ[] on 2010-06-02
> **Freiberg said:**
> I tried that, but I got "E: Couldn't find package 'sun-java6-plugin'."  Anything else I could try?

same think happens to me.

---

### Post by apoth on 2010-06-08
> **'Russ[] said:**
> same think happens to me.

Happened to me too, run this first:

```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner" && sudo aptitude update
```

---

### Post by pedro_orange on 2010-06-08
> **apoth said:**
> Happened to me too, run this first:

```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner" && sudo aptitude update
```

It's there once you add the partner repo:

```
pedro@pedro-desktop:~$ apt-cache search sun-java
sun-javadb-client - Java DB client
sun-javadb-common - Java DB common files
sun-javadb-core - Java DB core
sun-javadb-demo - Java DB demo
sun-javadb-doc - Java DB documentation
sun-javadb-javadoc - Java DB javadoc
sun-java6-source - Sun Java(TM) Development Kit (JDK) 6 source files
sun-java6-jre - Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)
sun-java6-javadb - Java(TM) DB, Sun Microsystems' distribution of Apache Derby
sun-java6-fonts - Lucida TrueType fonts (from the Sun JRE)
sun-java6-plugin - The Java(TM) Plug-in, Java SE 6
sun-java6-jdk - Sun Java(TM) Development Kit (JDK) 6
sun-java6-demo - Sun Java(TM) Development Kit (JDK) 6 demos and examples
sun-java6-bin - Sun Java(TM) Runtime Environment (JRE) 6 (architecture dependent files)
ia32-sun-java6-bin - Sun Java(TM) Runtime Environment (JRE) 6 (32-bit)
pedro@pedro-desktop:~$ 

```

Also as a side note. If you just want to enable all the non-open source stuff (Java, Flash, mp3, fonts, codecs etc) the best way to do it just to do:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by luminos77 on 2010-07-20
This way is probably the easiest.  

You absolutely NEED the java JDK package, but I will get to that shortly.  Also it is important to note that mozilla is attached to google chrome.  Whatever plugins you have in mozilla will show up identically in google chrome.  

1)   Go to Synaptics package manager and remove any jre or jdk main package.  The main packages will have extra components                                                                        attached to it, but Synaptic will take care of that for you, telling you what will be removed or added in a popup window.  Also make sure every java plugin is removed, type about:Plugins in the box where you would place a web address in mozilla.

2)   Verify java by going here: 

[http://www.java.com/en/download/installed.jsp]("http://www.java.com/en/download/installed.jsp")

Nothing should appear and the verify will not work.  If it does, not all java versions have been removed.

3)   Download the JDK package from java's site NOT synaptic, ubuntu software center, or terminal.

[http://java.sun.com/javase/downloads/index.jsp]("http://java.sun.com/javase/downloads/index.jsp")

If you are using ubuntu do not pick the rpm.  

4)   Follow instructions to install jdk here if you are new to ubuntu.

[http://java.sun.com/javase/6/webnotes/install/jdk/install-linux-self-extracting.html]("http://java.sun.com/javase/6/webnotes/install/jdk/install-linux-self-extracting.html")

If you find this link outdated when you read this the information can be easily found on the jdk site.

5)   Verify java again, it should work, if not try 4) again.  Then shutdown all google chrome and mozilla browsers!

6)   Follow instructions to setup plugin!

[http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html]("http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html")

The instructions say you need to create a symbolic link.  If you need a full path to get to the plugins folder (I know I did) it should be this 

/usr/lib/mozilla/plugins

The expanded path for <JRE>/lib/i386/libnpjp2.so is 

(downloaded package location)/jdk(version)/jre/lib/i385/libnpjp2.so

7)  Open mozilla then go to about:Plugins in mozilla and java will appear.

 Realize that google chrome could have organized this A LOT better instead of having millions of users shake their heads! LOL  enjoy java in google chrome!

---

### Post by a.kyppo on 2010-07-29
try sudo apt-get update and then try to install java-plugin

---

### Post by X.Cyclop on 2010-08-08
luminos77, it's hard (if possible) to uninstall all java instances, because of OpenOffice dependencies (OpenJDK...).
I just did what says on this page and it worked: [http://tatshuya.blogspot.com/2010/04/enable-java-plugins-for-google-chrome.html](http://tatshuya.blogspot.com/2010/04/enable-java-plugins-for-google-chrome.html) (from **[this thread]("http://ubuntuforums.org/showthread.php?t=1513370")**).;)

---

### Post by worksofcraft on 2010-08-08
There is guide for setting up latest Java with advanced 3D graphics capability at this game web site:
[http://services.runescape.com/m=forum/forums.ws?25,26,496,58594335](http://services.runescape.com/m=forum/forums.ws?25,26,496,58594335)

---

### Post by luminos77 on 2010-08-11
> **X.Cyclop said:**
> luminos77, it's hard (if possible) to uninstall all java instances, because of OpenOffice dependencies (OpenJDK...).
I just did what says on this page and it worked: [http://tatshuya.blogspot.com/2010/04/enable-java-plugins-for-google-chrome.html](http://tatshuya.blogspot.com/2010/04/enable-java-plugins-for-google-chrome.html) (from **[this thread]("http://ubuntuforums.org/showthread.php?t=1513370")**).;)

Yeah I meant just the main java packages, not all the little guys ha.  The website you used is definitely the shortcut method!

---

### Post by PeteLong on 2011-02-11
I know this is a very old thread but for Ubuntu 10.10 Desktop you can simply do [this]("http://www.petenetlive.com/KB/Article/0000395.htm")

Pete

---

### Post by Cavsfan on 2011-02-11
Or check the links in my signature. I have been using them successfully for a year or more.
The one on the left will tell you if you're up to date and the other one will provide exact instructions on how to install either 
the 32 bit java (left side of page) or the 64 bit java (right side of page).

---

### Post by Molech on 2012-05-18
Add the repository listed in [http://www.duinsoft.nl/packages.php?t=en]("http://www.duinsoft.nl/packages.php?t=en") and be happy. Working fine with Precise Pangolin x64 and Chrome (JRE 7u4).

---

### Post by oldos2er on 2012-05-18
Old thread closed. Please don't bump old threads.

---

