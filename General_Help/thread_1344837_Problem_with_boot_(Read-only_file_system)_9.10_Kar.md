---
title: "Problem with boot (Read-only file system) 9.10 Karmic .Pls Help"
date: 2009-12-03
forum: General Help
---

### Post by claudiu_upt on 2009-12-03
Hello 
I have a computer with 2 hard disks inside.A double boot: one with Ubuntu and the other with WinXp.There was a minor problem for me because a partion from the the xp drive was allways shown on my desktop at boot in ubuntu.I have to say that i don't really know what have i done wrong but i remember that i went in "device manager" i belive....and from ther i had 2 options..one regarding the xp drive and the ohet regarding the ubuntu drive.I changed so that the xp partition wil not pop again on desktop at boot....but of course i had to do more :-| .... i made some changes to the other drive(with ubuntu)..needless to say that i was very quick so i can't remember what i've done there)..but when i restarted my computer here it is what happened.

[CENTER]**After restart i got:**
[[img]http://img215.imageshack.us/img215/3713/picture002kp.th.jpg[/img]](http://img215.imageshack.us/i/picture002kp.jpg/)

**I did not know what that meant so i rebooted and got the login:**
[[img]http://img18.imageshack.us/img18/5229/picture003ig.th.jpg[/img]](http://img18.imageshack.us/i/picture003ig.jpg/)

**After login i get:**
[[img]http://img18.imageshack.us/img18/4222/picture004ye.th.jpg[/img]](http://img18.imageshack.us/i/picture004ye.jpg/)

**Then i tryed the recovery mode:**
[[img]http://img10.imageshack.us/img10/3200/picture005pt.th.jpg[/img]](http://img10.imageshack.us/i/picture005pt.jpg/)

**The i get the following:**
[[img]http://img259.imageshack.us/img259/1769/picture006ka.th.jpg[/img]](http://img259.imageshack.us/i/picture006ka.jpg/)

**I even tryed startx command and:**
[[img]http://img265.imageshack.us/img265/6030/picture123nd.th.jpg[/img]](http://img265.imageshack.us/i/picture123nd.jpg/)


So my file system is readonly....i don't know what to do next....
I can try to boot into a live cd but from there ...again i do not know...
Pardon my english mistakes...and please help my with a step by step guide...
I really hope i can avoid reinstalling the hole OS....
My experience with Ubuntu is about 1 year ...if that counts...so pls help...


**Regards Claudiu**
[/CENTER]

---

### Post by claudiu_upt on 2009-12-03
Anyone? :(

---

### Post by deranjer on 2009-12-04
I am having the exact same problem.  I will post back here if I get it resolved, please post here if you get yours resolved... I am considering doing a complete reinstall at this point.. right now I am attempting to use fsck to see if that will "solve" the hard drive problem... I am not a very savvy linux user, but it appears the file system got corrupted somehow?

---

### Post by deranjer on 2009-12-04
Well, in the maintenance shell I ran ```
fsck
``` and it ran through a file system check, then said "File system has been modified.  Please reboot." So I rebooted, and as it was rebooting it gave the error that it was unable to write to the X11.conf file, but after reboot it worked perfectly.  Hopefully this solves your problem.

---

### Post by claudiu_upt on 2009-12-05
When it enters the tty login you put your username and password and after that:

**mount -n -o remount,rw /**

then it should enter the login

after that you should edit:

**sudo nano /etc/fstab**

now and the partition that was the boot partition for my is sda1 you change puting this instead:

**/ ext4        errors=remount-ro    0    1**
**ctrl+x** and confirm by pressing** Y **
after a reboot the problem should be solved

You should now get back your login

Cheers....

---

