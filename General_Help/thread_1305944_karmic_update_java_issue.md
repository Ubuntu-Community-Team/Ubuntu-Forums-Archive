---
title: "karmic update java issue"
date: 2009-10-30
forum: General Help
---

### Post by yzarc on 2009-10-30
Dears,

I just made the update to karmic and now I having some problem with java. My version on jaunty was sun-java 6-16 but in karmic the available version is the 6-15.

My problem is that I can't install java-plugin and java-sdk because their version (6-15) is not compatible with the already installed java-bin and java-jre (6-16) legacy of the jaunty.

I thought in uninstall all java packages and reinstall the version 6-15, but to take them out I need to uninstall lots of dependent packages.

Does anyone know how to workaround this issue?

---

### Post by phillw on 2009-10-30
> **yzarc said:**
> Dears,

I just made the update to karmic and now I having some problem with java. My version on jaunty was sun-java 6-16 but in karmic the available version is the 6-15.

My problem is that I can't install java-plugin and java-sdk because their version (6-15) is not compatible with the already installed java-bin and java-jre (6-16) legacy of the jaunty.

I thought in uninstall all java packages and reinstall the version 6-15, but to take them out I need to uninstall lots of dependent packages.

Does anyone know how to workaround this issue?


I also upgraded (not fresh install)

I show  java-plugin   6-16-0ubuntu1.6.04
java-sdk  > java-gcj-compat is a collection of wrapper scripts, symlinks and jar
files.  It is meant to provide a Java-SDK-like interface to the GCJ tool
set.
1.0.80-1

java-bin  as per java-plugin
java-jre  all showing 6-16, as well.

What do you have showing ?

Phill.

---

### Post by yzarc on 2009-10-30
my problem is that I have sun-java-jre and bin installed with version 6-16 from jaunty, and now I can not install the sun-java-jdk and pluging because the version 6-16 is not available in karmic (although it was in jaunty). only the version 6-15 are showed in the synaptic for not install packges.

I believe that everyone who upgrade from jaunty won't can add any sun-java-* package if he had some sun-java-* already installed in jaunty. maybe that is a bug.

---

### Post by mousestalker on 2009-10-31
I'm running 64 bit karmic and I think the upgrade broke my java. Tried removing it and reinstalling and now it's all rather messy.

If I get more energy I'm probably going to tar my home folder and just do a fresh install. Or I may watch sports. :)

Addendum: I took the lazy way out and installed Opera. It can find the JRE just fine and life is good.

---

### Post by skpendurti on 2009-11-03
:o I have recently installed Karmic Kaola and installed the Java. Surprisingly, after the installation and restart of the system, my PC is showing the Java 1.6.0_15-b03 version of JRE in the terminal. And when I go to the [www.Java.com/en/]("http://www.Java.com/en/") and clicked on the "Do I Have Java on my PC" Link it says "Oops...you currently don't have the latest version of Java Installed on your system. The latest vesion is Java 1.6.0_16". I tried to install the self extracting package of latest java vesion given there, but, was helpless in updating so. I guess everyone is facing the same issue. Just want to mention that the Ubuntu 9.10 seems to have little complications with the new java plugin installer. It never gets installed. :(

---

### Post by utkjamie on 2009-11-04
Same problem. Had to uninstall and reinstall Firefox and Xulrunner because Firefox 3.5 wasn't launching external apps after upgrade to Karmic. In doing that, I lost the Java plugin and now can't reinstall it due to the version conflict.

---

### Post by macozz on 2009-11-09
The same here! So, I cannot use any banking site since all them here use java virtual keyboards!

---

### Post by scouser73 on 2009-11-09
For installing the 32 & 64 bit version of Java please follow the instructions [[COLOR="Red"]**Here**[/COLOR]]("http://sites.google.com/site/easylinuxtipsproject/java")

Although on the site it states that it's only for Ubuntu 9.10, I have installed it on Ubuntu 9.04 and it works flawlessly.

---

### Post by yzarc on 2009-11-09
my workaround was to umnistall all sun-java-* and reinstall them. to do this I use synaptic.

1. mark the installed sun-java* packages to umnistall, he will ask you to unistall other packages too. say yes.

2.DONT APPLY changes yet, go into menu file and save marks as. it will place wall packages mark to remove in a file.

3.apply

4. open the generated file with gedit  and replace umnistall by install and save it.

5. now load the file in synaptic. it will mark those packages to install

6. add to install  your extra sun-java* packages 

7. apply

---

