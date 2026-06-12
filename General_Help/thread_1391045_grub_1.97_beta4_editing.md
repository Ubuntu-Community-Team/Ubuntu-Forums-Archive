---
title: "grub 1.97 beta4 editing"
date: 2010-01-26
forum: General Help
---

### Post by konsta82 on 2010-01-26
I have grub 1.97 on carmic , with too many items in it. Start up manager , great for hardy and jaunty , is not working. What is the best way to remove unneeded items and change wait time for grub ?
Some suggestions ?

---

### Post by garvinrick4 on 2010-01-26
> **konsta82 said:**
> I have grub 1.97 on carmic , with too many items in it. Start up manager , great for hardy and jaunty , is not working. What is the best way to remove unneeded items and change wait time for grub ?
Some suggestions ?

If you really want to remove them completely use Synaptic in System/Admin/Synaptic
Type in box in upper right corner. Mark for completly remove and apply. Why not just remove
from system not completly and then do a "sudo apt-get clean" in terminal without quotes and
remove file from system that way. Incase you want it again it is there to install from repositories.

Wait time for grub: etc/default/grub as root and change grub-timeout from 10 to what ever you want.
Wait indefenitly with no time is -1

---

### Post by konsta82 on 2010-01-26
Sounds good , but that will not change my wait time in grub.
I just realized in synaptic there are both grub 0.97 and 1.97 installed. Can I remove 1.97 there and use old good grub 0.97 with startup manager ?

---

### Post by konsta82 on 2010-01-26
Something is weird.
In synaptic,I removed everything related to 2.6.31-14 (kernel I don't need) and cleaned but it is still there on startup.
file etc/default/grub is empty ?

---

### Post by oldfred on 2010-01-26
Did you do an upgrade or a clean install. Upgrades kept grub legacy but actually download the  grub2 package so it is available. You can go back to old grub if you really want to but have to be careful to remove all the parts of grub2 or you will have booting issues.

After any change you also need to run this:
sudo update-grub

To see your installed version:
Grub version
grub-install -v

Info on grub2:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Herman's pages on Grub2
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)
GRUB 2: A Guide for Users 
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

Not normally recommended:
HowTo: Revert from grub2 to Legacy Grub. 
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

### Post by hhlp on 2010-01-26
find in synaptic the following :

linux-image

and unistall old kernel

---

