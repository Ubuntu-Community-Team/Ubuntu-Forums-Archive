---
title: "I'm having trouble installing new programs."
date: 2010-01-27
forum: General Help
---

### Post by ejsholly on 2010-01-27
Actually, I'm not even sure how to install new programs on my Ubuntu.
 
First off, I'll just add that I'm a sophomore college student with a computer science minor, and while computers are pretty familiar to me, the Linux environment and experience is completely new to me.
 
I downloaded and installed Ubuntu last night and so far have really liked what I've experienced. However, I'm not sure how to install programs. I'm taking a Java course right now, and we're using Eclipse to write our programs, and when trying to install Eclipse, all I managed to do was download an Eclipse folder with a bunch of miscellaneous stuff (such as eclipse updates, but not the eclipse program itself).
 
How do I install an actual program instead of just the files that I did download?

---

### Post by konqueror7 on 2010-01-27
you may have downloaded Eclipse from the website, i believe there is a readme inside, or an executable in the folder....

Eclispe is also available in the repos, you may issue the following command in a terminal,```
sudo apt-get install eclipse sun-java6-jdk sun-java6-plugin sun-java6-fonts 

```

this will install Java and Eclipse...

you may further read [here]("https://help.ubuntu.com/community/InstallingSoftware") regarding installing applications...

---

### Post by kdaemon on 2010-01-27
Very quick answer:

see here for installing Eclipse:

[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

Use the Ubuntu Software Center for installing new applications from the repositories or open a terminal and type "sudo apt-get install <Package name>"

You can also download deb package files and double click them to install or use dpkg/apt from the command line

You can download apps in RPM format and convert them to deb files for installation using the alien utility

You can install from source files using:

./configure

make

sudo make install

As your so new to Ubuntu take some time to read up, well worth it and a massive time saver

---

### Post by Zaki ur Rehman on 2010-01-27
Hi Ejsholly
why dont you just go to Applications> Ubuntu software Center and select programming. You will find eclipse there, just select it and install.

---

