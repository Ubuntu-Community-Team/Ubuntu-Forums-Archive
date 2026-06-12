---
title: "Working solution, partition manager doesn't detect harddrive or other os"
date: 2009-11-25
forum: General Help
---

### Post by Divider on 2009-11-25
I was having an issue with my Harddrive not being detected when attempting to install ubuntu 9.10. To fix it you need to do 2 things.

First, go into live cd mode,  your gonna need to use the terminal.

Next. Enter this into a terminal and then start the installation process normally.

```
sudo apt-get remove dmraid
```

after doing this, the partition manager in the installation menu will see your drives. My motherboard didn't have raid enabled, but for some reason this package loaded. Hope this helps anyone else.:popcorn:

---

### Post by kisufox on 2009-12-28
Thank you so much for this work around. I was about to rip my hair out because I couldn't install.

---

### Post by Jetcollins on 2010-02-04
Thanks very much. This worked for me, also :KS

---

### Post by deadguy on 2010-02-09
I'm trying to install ubuntu server with raid enabled.  If I choose to activate the raid devices, no disks are detected and I cannot continue installation.  If I do not activate, both disks (of my raid 1) are listed.  Does this mean raid is broken in 9.10?

---

### Post by nextraa on 2010-05-05
Hasn't worked for me.

ubuntu@ubuntu:~$ sudo apt-get remove dmraid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package dmraid

Have to searched further why my harddrive isn't detected.

---

