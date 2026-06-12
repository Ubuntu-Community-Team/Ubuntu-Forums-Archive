---
title: "Blank screen after dist-upgrade"
date: 2011-09-04
forum: General Help
---

### Post by FLCL on 2011-09-04
Ubuntu 10.10
I was working on getting iPhone4 support in Rythmbox because I was getting an unknown device and then it would unmount. 
I updated libimobiledevice1 and installed libimobiledevice-dbg, then ran ```
sudo apt-get dist-upgrade
``` after.
Rebooted, and after load up I get a blank/black screen instead of a log in screen. 

Rebooted, same thing. Sometimes I don't even see the Ubuntu splash as it loads, it just prints out some lines as if it were in verbose mode and then blank screen. Currently running in failsafeX graphics mode.

---

### Post by FLCL on 2011-09-04
This was solved by the following:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure -phigh xserver-xorg
```

courtesy of Rubi1200, found [HERE]("http://ubuntuforums.org/showthread.php?t=1670431")

---

