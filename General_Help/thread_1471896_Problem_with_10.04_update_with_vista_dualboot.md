---
title: "Problem with 10.04 update with vista dualboot"
date: 2010-05-03
forum: General Help
---

### Post by Physicsnerdely on 2010-05-03
I am fairly new, so needless to say I broke something by being dumb.
I previously ran and hopefully will again very soon, Ubuntu and Vista dual boot with grub being the primary bootloader.
So, I just updated 10.04 today and when a window appeared asking things something along the lines of where to install grub, I didn't know what to do. So after reading the help box say that if you're not sure (which I was not) to click all of them, I did just that. Now when I go to the vista option in grub all that appears is a blinking cursor followed by bleak disheartening nothing until restarting. I can boot into ubuntu just fine and can still mount the windows partition from inside of ubuntu, but cannot boot Vista.

I had read other threads that usually asked for the user to run "sudo fdisk -l", to which the results are:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44dc8e43

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30402   244196352    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x40366a30

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18662   149902483+  83  Linux
/dev/sdb2           18663       19457     6385837+   5  Extended
/dev/sdb5           18663       19457     6385806   82  Linux swap / Solaris

Also someone directed another user to /mnt to look for windows related files, which in my case are there. Suggestions, and solutions would be greatly appreciated, but more importantly pointing out what and how I broke it will help me in the future. Thanks community!

---

### Post by itiswhatitis on 2010-05-03
Ran into the same option here...

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

That link has instructions on how to fix.

---

### Post by techunit on 2010-05-03
Wasn't this problem fixed in an update that was pushed in the release of ubuntu. If you were running a RC then this would make sence but at the moment I am at a loss to explain it. Ok I looked at the page provided by itiswhatitis and I think that for you just putting:

```
sudo update-grub
```

this is should do the trick. If that doens't do it for you the look at the link in the post above.

---

### Post by oldfred on 2010-05-04
This is what the instructions say (bold by me):

If you're unsure which **drive** is designated as boot drive by your BIOS, it is often a good idea to install GRUB to all of them.         

It also says:
Note: It is possible to install GRUB to **partition** boot records as well. However, this forces GRUB to use the blocklist mechanism, which makes it less reliable, and therefore is **not** recommended.

It then presents a check box with all drives and partitions. So everyone (And I think it is everyone) checks all the boxes. Only drives sda, sdb, etc should be checked. Not partitions sda1, sda2, sdb1, etc.

Installing to the windows partition overwrites part of the windows boot that is already in the windows boot sector or PBR.

---

### Post by Physicsnerdely on 2010-05-04
Thanks a ton, The first thread was the solution, and the third was exactly what the boxes I was haphazardly clicking on stated. All is well now, and thank you very much.

---

### Post by techunit on 2010-05-04
your welcome... pretty much any problem with the GRUB menu can be solved by updating it. This deosn't all ways work but it is the first thing I always try...

---

### Post by Alfred_Jodocus on 2010-05-28
The solution as described in the link, using 'testdisk', worked for me too.

My win-2000/Ubuntu 10.04 dual-boot system stopped working, after I updated from Ubuntu 9.10 to 10.04. I too ticked all boxes to install GRUB to (because that is what the accompagnying information appeared to mean to me). 

After installing testdisk and doing exactly what it said in the link, Win-2000 works again, fortunately.

This particular issue (selecting the right boxes/places to install GRUB on) deserves more clarification in a next release; I'm sure I'm not the only one who took the explanation the wrong way and selected *all* boxes/locations (partitions), as opposed to just physical drives.

---

### Post by oldfred on 2010-05-28
Those working on Ubuntu rarely if every come here to see issues. The do look at the bug reports and kansasnoob has created one. the only way to get things fixed it to have a lot of those who have the issue sign up and add to the problem count.

Kansasnoob bug report:
[http://art.ubuntuforums.org/showthread.php?t=1475385](http://art.ubuntuforums.org/showthread.php?t=1475385)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

---

