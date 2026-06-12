---
title: "Boot problem"
date: 2010-04-04
forum: General Help
---

### Post by loganbook201 on 2010-04-04
I recently installed ubuntu 9.10.  Restarted my system and this comes up:


Ubuntu 9.10 logan-desktop tty1

logan-desktop login:

Really confused as to whats going on.
If I use my nvidia 8400gs its come up with the same screen, but in 800x600 resolution.
Using the onboard it goes to 1280x1024 with the same screen.:confused:

Help me guys!

---

### Post by Sin@Sin-Sacrifice on 2010-04-04
That's the login screen but on CLI (command line terminal). When it asks for your login info type it in and you'll get your command prompt. Once there type ```
startx
``` and hit enter. If the GUI (graphical user interface) doesn't come up then post the output (copy whatever it says after you hit enter and post it here).

---

### Post by 3rdalbum on 2010-04-04
> **Sin@Sin-Sacrifice said:**
> That's the login screen but on CLI (command line terminal). When it asks for your login info type it in and you'll get your command prompt. Once there type ```
startx
``` and hit enter. If the GUI (graphical user interface) doesn't come up then post the output (copy whatever it says after you hit enter and post it here).

Make that:

```
sudo service gdm start
```

---

### Post by loganbook201 on 2010-04-05
Im typing this from a laptop not my desktop, since I can't get to any sort of gui.
 
ubuntu 9.10 logan-desktop tty1
 
logan-desktop login: logan
password:********
Last login: Sun Apr 4 22:55:53 CDT 2010 on tty1
linux logan-desktop 2.6.31-14-generic #48-ubuntu SMP Fri OCT 16 14:04:26 UTC 2009 i686
 
to access official ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
 
233 packages can be updated.
84 updates are security updates.
 
logan@logan-desktop:~$ sudo service gdm start
[sudo] password for logan: **********
gdm start/running, process 1663
logan@logan-desktop~$ startx
fatal server error:
no screens found
 
This happened to me last time until i reinstalled.

---

