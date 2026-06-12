---
title: "Permissions to write to mounted partitions"
date: 2006-03-05
forum: General Help
---

### Post by StandardDeviant on 2006-03-05
Hello, I've had Ubuntu as a dual-boot with WinXP for a few months now, but haven't been able to use it because of what seems to be a simple problem that I just can't solve.

I have 3 partitions that I use on my computer:  An NTFS partition for XP, a Linux partition for Ubuntu, and a FAT32 partition for my documents and personal files, so that I can access my files from either OS.  I can read and write to the FAT32 partition just fine from XP, but Ubuntu is another story - I can read from it, but not write to it.

The partition in question is /dev/sda7, mounted as /media/sda7.  I've tried editing my /etc/fstab to allow writing, but that's no go - it doesn't let me save (presumably because I'm not logged in as root?)  Also, chmod doesn't work, it says I don't have permission to change it.

However, when I go into the root terminal and use
```
gksudo nautilus
```
I can write to /media/sda7.  But I'd much rather just double-click on the sda7 icon that's on my desktop.  So what should I do for this?

I've Googled the problem, and have tried everything that I found, and nothing works so far.  And it's pretty rough, since I'm doing this on a laptop with only a dialup connection to the internet, and booting Ubuntu takes about 10 minutes because it halts at the part where it checks the network connection, and waits for the network interface to come up, giving up after quite a while.  Is there a way I can disable this behavior so that this problem can be solved much more quickly?

---

### Post by Sutekh on 2006-03-05
This link has a really good explanation for mounting Windows partitions NTFS and FAT32

[Mounting Windows in Ubuntu - by ]("http://www.psychocats.net/linux/mountwindows.php")[aysiu]("http://www.ubuntuforums.org/member.php?u=21941")

---

### Post by xmastree on 2006-03-05
[QUOTE=StandardDeviant]minutes because it halts at the part where it checks the network connection, and waits for the network interface to come up,[/QUOTE]Try pressing Ctrl-C when it reaches that point to skip it.

---

### Post by vayu on 2006-03-07
Follow the instructions given by aysiu in the link above, then if you still don't have write access maybe you need to reset the dos read only attribute in windows:
[http://www.ubuntuforums.org/showthread.php?t=140809]("http://www.ubuntuforums.org/showthread.php?t=140809")

---

