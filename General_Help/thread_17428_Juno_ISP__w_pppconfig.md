---
title: "Juno ISP  w/ pppconfig"
date: 2005-02-28
forum: General Help
---

### Post by sophiamld on 2005-02-28
How can I get pppconfig to make Juno work? I tried a few times, it connected, and then immediately disconnected.
I have the Juno .deb file, I made it into a .tar file . . . but from there I still don't know where to go. I've put everything in where I think the "right" places are, but no luck.
I realize Juno is sort of a stupid ISP (as are any ISPs that "require" a program to make it work) but I'm not about to ask my mom to switch it. She wouldn't be too willing.

---

### Post by RastaMahata on 2005-02-28
[QUOTE=sophiamld]How can I get pppconfig to make Juno work? I tried a few times, it connected, and then immediately disconnected.
I have the Juno .deb file, I made it into a .tar file . . . but from there I still don't know where to go. I've put everything in where I think the "right" places are, but no luck.
I realize Juno is sort of a stupid ISP (as are any ISPs that "require" a program to make it work) but I'm not about to ask my mom to switch it. She wouldn't be too willing.[/QUOTE]
 someone move this thread. The howto forum is not for asking questions :s

---

### Post by littlefish on 2005-03-02
I am still waiting for my Ubuntu CD, and I am a newbie.  But I have been playing around with Mepis.  I got Juno working in mepis.  It uses KDE so this may be completely different in Gnome.  But maybe someone can tell you how to do it in Gnome.

First I installed the Juno deb file (as a deb - can't Ubuntu do this? It is debian based - isn't it?)  I think that I used kpackage, but I am sure that you can also use synaptic and point to the juno deb file. 

The juno creates an icon on the root desktop (as it was designed for Lindows and Lindows runs as root).  It also creates a /opt/juclient folder (or something like that).  If you right click on the desktop icon or the juclient folder, then click on the properties, then the permissions tab you will see that they are owned by root and belong to the group "root".  They are also write protected for everyone but the owner (which, of course, is root).  Inside of the juclient folder is a lot of settings files and its own ppp dialer program.

I got juno to work by the following:

1. log in as root
2. copy the juno icon from the root desktop to the user desktop (in mepis /home/username/desktop)
3. change the group for the icon to "users"
4. change the group for the entire juclient folder to "dialout" (is this different in Ubuntu - maybe "dialup"?), and giving read and write permissions to the group.  I did this by rightclicking the folder, selecting properties, selecting the permissions tab, changing the group to "can read and write," changing the group to "dialout," and selecting the checkbox that says to apply settings to all files within the folder.

After all of this, everything worked, and it dials up and works every time.

I am assuming that your modem is dialing with the Juno program (sounds like it).  If it is not, Juno expects that your modem is at /dev/modem.
Mepis has two kernel options (a 2.4 and a 2.6 kernel), and I noticed that the Juno program does not seem to work on the 2.4 kernel.  It dials, connects, and I can even get a web page for a few seconds, then it exits with an error.  I installed the Juno program using the 2.6 kernel, so maybe it has something to do with that.

I really don't understand all of this stuff entirely.  I just know what seemed to work for me.  I think I read somewhere, that someone got things working by just changing the read/write permissions on the stuff in the juclient folder, so maybe all of the things I did are not necessary.

Good luck. :lol:

BTW -- Juno will ONLY work with the Juno dialer, because they have a proprietary dialer program.  I believe it encrypts the username and password, but I don't know this for sure.  I think there are some programs on the internet that will get the real userid / password for you, but I believe it is illegal to do it this way.

---

### Post by sophiamld on 2005-03-03
[QUOTE=littlefish]I am still waiting for my Ubuntu CD, and I am a newbie.  But I have been playing around with Mepis.  I got Juno working in mepis.  It uses KDE so this may be completely different in Gnome.  But maybe someone can tell you how to do it in Gnome.

First I installed the Juno deb file (as a deb - can't Ubuntu do this? It is debian based - isn't it?)  I think that I used kpackage, but I am sure that you can also use synaptic and point to the juno deb file. 

The juno creates an icon on the root desktop (as it was designed for Lindows and Lindows runs as root).  It also creates a /opt/juclient folder (or something like that).  If you right click on the desktop icon or the juclient folder, then click on the properties, then the permissions tab you will see that they are owned by root and belong to the group "root".  They are also write protected for everyone but the owner (which, of course, is root).  Inside of the juclient folder is a lot of settings files and its own ppp dialer program.

I got juno to work by the following:

1. log in as root
2. copy the juno icon from the root desktop to the user desktop (in mepis /home/username/desktop)
3. change the group for the icon to "users"
4. change the group for the entire juclient folder to "dialout" (is this different in Ubuntu - maybe "dialup"?), and giving read and write permissions to the group.  I did this by rightclicking the folder, selecting properties, selecting the permissions tab, changing the group to "can read and write," changing the group to "dialout," and selecting the checkbox that says to apply settings to all files within the folder.

After all of this, everything worked, and it dials up and works every time.

I am assuming that your modem is dialing with the Juno program (sounds like it).  If it is not, Juno expects that your modem is at /dev/modem.
Mepis has two kernel options (a 2.4 and a 2.6 kernel), and I noticed that the Juno program does not seem to work on the 2.4 kernel.  It dials, connects, and I can even get a web page for a few seconds, then it exits with an error.  I installed the Juno program using the 2.6 kernel, so maybe it has something to do with that.

I really don't understand all of this stuff entirely.  I just know what seemed to work for me.  I think I read somewhere, that someone got things working by just changing the read/write permissions on the stuff in the juclient folder, so maybe all of the things I did are not necessary.

Good luck. :lol:

BTW -- Juno will ONLY work with the Juno dialer, because they have a proprietary dialer program.  I believe it encrypts the username and password, but I don't know this for sure.  I think there are some programs on the internet that will get the real userid / password for you, but I believe it is illegal to do it this way.[/QUOTE]
 Thanks a lot for telling me that Juno won't work without the Juno dialer. That will save me a lot of time! I've been trying other dialers too much, and well, now I won't anymore.

The version of Ubuntu I have isn't too friendly with .deb files (but Hoary Hedgehog is supposed to handle those better) but it seemed to install all right using file-roller. After that, I did everything you said. Double clicking the desktop icon under root or my user didn't work . . . nothing happened.

When I try running "/opt/juclient/nzppp -c" which is the command to connect this message shows up:

[B]Dialing. . .
rm: cannot remove `./dat/localppp': No such file or directory
rm: cannot remove `./dat/localppp': No such file or directory
/usr/sbin/pppd: Can't open log file /dat/localppp: No such file or directory[/B]

This file does indeed exist, in fact this "dialer" (nzppp) recreates it every time it's executed.

I'm sort of stumped now. Until then, I think I'm going to wait until I can get a copy of Hoary Hedgehog or Mepis . . . though without the internet, it'll be tough (hehe.)

Thanks for your help though. Even though my problem hasn't been solved, you cleared up a lot for me. I'm very new to Linux.

**NOTE: Sorry for posting here. I wanted to try to delete my message before littlefish replied, but I never figured out how. I won't create any new threads without reading the thread terms more clearly.** 

Sophia

---

### Post by littlefish on 2005-03-03
You can buy a cd for Warty, or other single disk distros online for really cheap ($2.50 with shipping).  Just search google, or debian has a list of sources for CDs (many of which sell many other distros like ubuntu.  

Does Ubuntu really have problems with DEB files?  I thought it was set up to use apt and synaptic (which should use deb files!)

Also, I think nzppp is the dialer, but I think it is controlled by some other program.  I read somewhere that the juno program uses Java (I don't know if this is true).  Does Ubuntu install Java by default, or do you have to apt-get it?  That may be your problem.

The following link has info on how to install Java in Ubuntu

[http://ubuntuguide.org/](http://ubuntuguide.org/)

or here

[http://www.ubuntulinux.org/wiki/Java](http://www.ubuntulinux.org/wiki/Java)

Of course, it may be hard to do without an internet connection.

I believe mepis uses Blackdown java.  I don't know what that means or what the difference is between that and Sun Java.

---

### Post by jdodson on 2005-03-04
howto is not the place to ask questions.  please read the forum rules before posting.

---

### Post by frank392 on 2006-06-29
Hi, I have posted the solution to make juno and netzero work with linux just go to:

[http://www.mepislovers.org/modules/newbb/viewtopic.php?viewmode=flat&topic_id=15025&forum=9](http://www.mepislovers.org/modules/newbb/viewtopic.php?viewmode=flat&topic_id=15025&forum=9)

if yoou have more questions please contact me

Frank

---

