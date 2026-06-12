---
title: "npviewer.bin eating up CPU"
date: 2010-04-30
forum: General Help
---

### Post by OMJD on 2010-04-30
Hi,

Since upgrading to 10.04, npviewer.bin has a habit of eating up my CPU (Q6600) resources whenever I watch a flash video. This is kinda annoying as I like to play music on Youtube while browsing the internet. 

I'm using Chrome 5.0.342.9 beta.

Any ideas?

Cheers

---

### Post by nanog on 2010-04-30
if you are using 64 bit you should go here: [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

---

### Post by GSF1200S on 2010-04-30
> **OMJD said:**
> Hi,

Since upgrading to 10.04, npviewer.bin has a habit of eating up my CPU (Q6600) resources whenever I watch a flash video. This is kinda annoying as I like to play music on Youtube while browsing the internet. 

I'm using Chrome 5.0.342.9 beta.

Any ideas?

Cheers

npviewer.bin also caused my system to use a ridiculous amount of CPU (im on an i7!). I dont know how to get adobe's 64bit flash working on Chrome, but I can say that I downloaded the 64 bit alpha version of flash from adobe's website for linux and it has performed flawlessly. I have had 0 crashes of firefox and all things flash work. I accomplished this by placing libflashplayer.so in a folder called Plugins in .mozilla. I then removed:
```
nspluginwrapper
```
and
```
flashplugin-installer
```
and have had no issues since. It has changed alot with time- flashplugin-installer might do the same thing for you.. I need to check. See this link for further details:
[http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)

Perhaps you could find out where chrome looks and place a copy there?

---

### Post by elefabio on 2011-02-23
Dear all,

I have installed firestarter (firewall manager) at my Ubuntu 10.04 64-bit desktop and I figure out that the npviewer.bin is sending data to 213.205.104.130 through ports 80, 443 and 1935. Is this okay?

Cheers,

Fabio

---

### Post by Rebelli0us on 2011-05-15
yeah Adobe Flash sucks. When I see high CPU usage, I go to System Monitor > Processes, right click on npviewer.bin and KILL it.

---

