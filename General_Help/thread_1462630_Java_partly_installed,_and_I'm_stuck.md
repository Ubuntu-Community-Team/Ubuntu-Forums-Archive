---
title: "Java partly installed, and I'm stuck"
date: 2010-04-25
forum: General Help
---

### Post by sa2u on 2010-04-25
I'm setting up a fresh install of Kubuntu 9.10. I need to install Java.  I searched the Web,  got the following command string, which I used:

 sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

All went well until it displayed the Sun user agreement. At the bottom of the shell window there was <OK>. I hit Enter. Nothing. I clicked on OK, but nothing. Nothing was below the OK in the shell screen. According to the directions, the script was supposed to finsh installing the Java components after I agreed to the license terms, but nothing more happened.

I tried running the above command again, but got an error message. I rebooted and tried again. The following message appeared:

swa@S6500NX:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-15-1) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-15-1) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
  sun-java6-plugin: Depends: sun-java6-bin (= 6-15-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
swa@S6500NX:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I was doing this cookbook style, and now I have no idea how to proceed.  

In that other OS, Firefox asked if I'd like to install Java. I clicked yes, and within two minutes or so it was downloaded and installed. In Kubuntu, I'm struggling with arcane commands in a DOS 5-style terminal window, 45 minutes into an ordeal and stuck but good.

Is there some way to remove what's been done so far and start the whole process over? Or would doing that just lead to the same sticking point at the end of the Sun license agreement?

Help with this would be greatly appreciated. Thanks.

---

### Post by QIII on 2010-04-25
In Synaptic, select them all for removal and get rid of them.

Then follow this guy's directions for getting the latest installed.  If I am not mistaken, the Java in the Karmic repos is Update 15 or 16, which have security problems.  Even 19 was causing problems for Windows users, allowing "drive-bys".

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Be sure you follow either the 32 bit or 64 bit directions as appropriate.


(By the way, it works in Windows because Oracle/Sun has made it that way.  They have not made it that way for Linux.  Not Linux' fault.)

---

### Post by sa2u on 2010-04-26
QIII, I had to use kpackagekit instead of Synaptic (or is that a front end for Synaptic?), but was able to scour out all the java-related items I had installed.

I followed the step-by-step directions you pointed me to, and they were excellent. Exactly what I needed.  I finally got the latest Java installed and verified.

I'm so grateful for your help.

BTW, from what you said about Sun tailoring Java installation for the other OS, I get the impression it's a case of major corporations scratching each other's backs. That comes as no surprise.  It would be decent if they were as accommodating for all their users, corporate or open source/GPL, what have you.

Again, thank you very much.:)

---

### Post by QIII on 2010-04-26
I was actually talking about the ease of Java installation.

Java itself is cross-platform and doesn't balk.

I use it in Windows, Linux and OpenSolaris.

It's just the ease of installation issue that is troublesome.  However, Lucid's partner repository has the latest version and it can be installed through the normal package management process, making it easy again.

---

