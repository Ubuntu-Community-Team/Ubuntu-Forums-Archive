---
title: "Stardate App?"
date: 2010-05-21
forum: General Help
---

### Post by ShadowGazer on 2010-05-21
This is sort of a weird question but...on the mac there is a piece of software to change the system clock so it shows the stardate instead of the month, day and year.  Is there something like that for Ubuntu?  I think it would be pretty cool to have a star trek themed desktop

---

### Post by akakingess on 2010-05-21
You could check out this system tray on sourceforge [here]("http://sourceforge.net/projects/stardatesystray/") , but that is just one of many possible options. As to the Star Trek theme idea, I would be shocked if there weren't one out there already, so you may want to check out gnome-look.org , and I would also suggest trying to create your own. It's a fun way to learn the system and get exactly what you want ;)

---

### Post by ShadowGazer on 2010-05-21
Tried installing that, and I get an error.

```
Error: Dependency is not satisfiable: sun-java6-jre
```

I'm kinda sorta new to Ubuntu linux, I've only played around with a few things, and not really sure about alot of error messages

---

### Post by akakingess on 2010-05-21
That just looks like you need to install the Java Runtime Environment, really just Java, at least version 6 or higher in order to run that system tray.  If I were you I would just go to sun.com/java and get the latest version of Java for Linux and install that. It can be a little tricky so pay close attention to the instructions that they give you on the site (and even sometimes printing them out so you have them in front of you while doing the install helps). After that, you should not have any problems with the Stardate System Tray or whatever it was called, but if you do let us know and we will try to help you through it. Also, the way I found that was by googling "stardate application for linux" and it came up with several links that you could check out.  Good Luck!

---

### Post by ShadowGazer on 2010-05-21
Okay, I've gotten so far as to "inflate" the java package I downloaded, but enabling it is a bit of a problem.  Can someone walk me through the instructions?  Here they are:

```
Firefox or Mozilla

   1. Create a symbolic link to the libjavaplugin.so file in the browser plugins directory
          * Go to the plugins sub-directory under the Firefox installation directory
            cd <Firefox installation directory>/plugins

          * Create the symbolic link
            ln -s <Java installation directory>/plugin/i386/
            ns7/libjavaplugin_oji.so

            In the ln command line above, use ns7-gcc29 if Firefox was compiled with gcc2.9.

      If you install Firefox 1.5 or later, you can enable the Java Console menu item in the Tools menu. Change directories to the Firefox extensions directory, then unzip ffjcext.zip there.

          cd /usr/lib/firefox-1.4/extensions
          unzip /usr/java/jre1.6.0/lib/deploy/ffjcext.zip 

      Example
          * If Firefox is installed at this directory:
            /usr/lib/firefox-1.4/
          * And if the Java is installed at this directory:
            /usr/java/jre1.6.0
          * Then type in the terminal window to go to the browser plug-in directory:
            cd /usr/lib/firefox-1.4/plugins
          * Enter the following command to create a symbolic link to the Java Plug-in for the Mozilla browser.
            ln -s /usr/java/jre1.6.0/plugin/i386/ns7/libjavaplugin_oji.so

   2. Start the Firefox browser, or restart it if it is already up.

      In Firefox, type about:plugins in the Location bar to confirm that the Java Plugin is loaded. If the version is Firefox 1.5 or later, click the Tools menu to confirm that Java Console is there
```

---

### Post by ShadowGazer on 2010-05-21
I wish it were easier to install java.  I don't really understand the instructions at all.  Every time I try to make a link to that file, it ends up not finding it or something.  I don't know how to explain it

---

### Post by akakingess on 2010-05-21
Sorry, I was out of the house when you responded, if you have java now installed, go to that directory and find the libjavaplugin.so file, or whatever it is called (it changes from one version to the next sometimes) and you can right-click on the .so file and select "Create Symbolic Link" which will create a "shortcut" of that same .so file. Then, you can cut/paste that 'shortcut' into your plugins folder for whichever browser/app that needs it, and if you can't find the plugins folder it may be hidden, for instance, Firefox has it's own hidden folder for config files and such and the folder will start with a period. You can go to your home folder and hit CTRL H and that will allow you to view the hidden files and folders. See what you can figure out with this info and then get back with me.

Actually, if you have java now installed, will the stardate system tray install, or will it at least tell you where to place the libjavaplugin file?

---

### Post by ShadowGazer on 2010-05-21
Okay, I went to the firefox directory, there was no plugins directory so I made one, placed the link in there, and it still doesn't work.  What am I doing wrong?

Also, no, apparently I just "inflated" the java, not installed it.  It made its own folder and such where I placed it but it didn't actually install java

---

### Post by akakingess on 2010-05-21
Was it a .mozilla folder? That's where the Firefox plugins folder is located. Like I said, it is going to be hidden, so you need to choose to view hidden files/folders and go into the .mozilla folder and paste/create the link in the plugins folder that should already be in the .mozilla directory.

---

### Post by ShadowGazer on 2010-05-21
Oh!  .mozilla directory, I actually went into the firefox folder after that.  I'll try putting the folder into the .mozilla directory this time!

---

### Post by akakingess on 2010-05-21
Cool, simple mistake, let me know how it turns out, you will  also need to put libflashplayer.so or a sym link of it in the same folder so get used to going there.

---

### Post by ShadowGazer on 2010-05-21
so far no go.  This is what I'm trying to put into the .mozilla directory, is this right?  Also, I can't find libflashplayer.so anywhere in my java installation directory, where do I look for that at?  Second screenshot is what my .mozilla folder looks like, is that right as far as directory structure and what not?

---

### Post by akakingess on 2010-05-21
Sorry to confuse the situation, the libflashplayer.so is the plugin for Flash, doesn't have anything to do with your java stuff, now, the screenshot with the libjavapluin.so (or whatever it's called) is what you want to right-click on and create a symbolic link of and then cut/paste that into the plugins folder (and you are in the correct directory). Now keep in mind that all this is going to do is install the java plugin for Firefox and may not have anything to do with your stardate system tray. You may need to look at the install directions for stardate and see if it needs that plugin link put somewhere else within your system, sometimes it will be in the file system, under usr/java, or something of that nature. Be aware that to do anything within the filesystem you need to have root powers (precede commands with 'sudo' and enter your password) so be very careful, however, if you installed Java according to Sun's instructions your system should sense that it has Java (JRE) installed.

---

### Post by ShadowGazer on 2010-05-21
Unfortunately it's a no go.  I tried running Java.com's java tester and it doesn't detect anything installed.  Ugh I wish someone could take over my computer and do it for me like you could on windows heh

---

### Post by sydbat on 2010-05-21
Why not just install java from the repository? System > Administration > Synaptic. No need to get overly complicated.

---

### Post by akakingess on 2010-05-21
Make sure that [this]("http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80") is the page that you went to to get java runtime environment, and make sure to get either the 32-bit or 64-bit one based on what Ubuntu you have installed. Also, it wouldn't hurt to also check your Synaptic Package Manager (go to System-->Administration-->Synaptic Package Manager) and do a quick search for JRE and you may be able to insall the version that comes with Ubuntu (should be at least version 6) and it is worth a shot anyway. So, try the package manager first, and then if for some reason that doesn't work, check the link that I put in this message and download and re-install and make sure it's the correct version and you extract it to the proper directories (if they exist, just create them, again you will probably need to have root privileges to do that). Let me know how that goes, I have to run 2 of my kids to friends houses, but will be back in about 20 mins.

---

### Post by ShadowGazer on 2010-05-21
Did a search for JRE in Synaptic and a whole mess of things pop up.  What exactly do I install?

---

### Post by sydbat on 2010-05-21
> **ShadowGazer said:**
> Did a search for JRE in Synaptic and a whole mess of things pop up.  What exactly do I install?sun-java6-jre

It'll want to install some dependencies...let it.

EDIT - and java-common too

---

### Post by 2hot6ft2 on 2010-05-21
There are 2 ways to go. The first is removing openjdk and the other is have both sun and openjdk installed and setting it to use the sun version. Since I've already covered both ways I'll just link to them. Don't let the title of the second one throw you off it is what I said.

First removing openjdk and installing suns version
[http://ultimateeditionoz.com/forum/viewtopic.php?f=73&t=1080&p=3878#p3878](http://ultimateeditionoz.com/forum/viewtopic.php?f=73&t=1080&p=3878#p3878)

Having both installed and setting it to use the sun version
[http://forumubuntusoftware.info/viewtopic.php?f=68&t=4594&start=10#p51578](http://forumubuntusoftware.info/viewtopic.php?f=68&t=4594&start=10#p51578)

Each has their reason for doing it that way, for one removing openjdk would remove other things that it shouldn't have so having both installed was the way to go in that case.
:guitar:

---

### Post by ShadowGazer on 2010-05-21
Thanks 2hot, that second link worked out perfectly and I now have java installed

---

### Post by 2hot6ft2 on 2010-05-21
> **ShadowGazer said:**
> Thanks 2hot, that second link worked out perfectly and I now have java installed
You're welcome. Glad it helped.
:guitar:

---

### Post by Bernmeister on 2012-06-25
FYI: I'm the author of the Java Stardate System Tray application.  I've created a new Python version which works on Ubuntu 12.04 (and Lubuntu/Xubuntu).

[https://launchpad.net/~thebernmeister/+archive/indicator-stardate]("https://launchpad.net/~thebernmeister/+archive/indicator-stardate")

---

