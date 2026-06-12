---
title: "Manage detection of (Windows) partitions"
date: 2010-01-04
forum: General Help
---

### Post by mart78 on 2010-01-04
Hello,
I'm running Ubuntu 9.10 together with Windows 7 and when I launch Nautilus I have a list of all my (Windows) partitions in the navigation bar on the left.
However I don't want to see all those partitions in Ubuntu (eg. the Windows system partition or the partition reserved for the Win boot loader.
Is there a way I can control which partitions will be detected and listed for mount in Nautilus?

---

### Post by s.fox on 2010-01-04
Hi,

I found [this]("http://ubuntuforums.org/showthread.php?t=668748") thread which may be of some use to you.

-Silver Fox

---

### Post by Morbius1 on 2010-01-04
It's ironic, but one way to make sure those partitions don't show up in "Places" and ready to mount is to mount them.

For example, If sda1 is the windows partition you could go into /etc/fstab and add a line that looks like this:

**/dev/sda1 /Windows/sda1 ntfs defaults,umask=777 0 0 **

You'd have to create the mountpoint first though:

**sudo mkdir /Windows/sda1**

Since it's not in /home or /media it won't show up under "Places"
The umask=777 will prevent anyone ( even root ) from reading or writing to it. And the 0 at the end will prevent linux from doing any kind of file system check on it.

If you want to go this way, post the output of the following command and someone can help you: **sudo blkid**

---

### Post by mart78 on 2010-01-05
Thanks for the replies, now I know how to get rid of my Windows drives ;) 
Still I'm surprised that there is no simpler way to do this like just remove them from Nautilus or sth.

---

