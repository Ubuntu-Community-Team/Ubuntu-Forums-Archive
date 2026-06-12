---
title: "Someone please help me!"
date: 2011-03-05
forum: General Help
---

### Post by Haylinux on 2011-03-05
oh my gosh. so today, i downloaded baldurs gate II shadows of amn iso's, because i lost one of the CD's to the box, but anyways, I went to mount the third .ISO for installation, and BAM! my computer froze, so i waited five minutes, came back, and still frozen. shut it down for 20 minutes, pulled it back up, and it's got this error as follows;
"Mount: mounting /dev/disk/by-uuid/65b0a6a-a366-435a-a086-58428cfe2bd1 on /root 
Failed: invalid argument
Mount: mounting /dev on /root/dev failed: no such file or directory
Mount: mounting /sys on /root/sys failed: no such file or directory
Mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have requested /sbin/init
No init found. try passing init= bootarg


BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)"
I'm willing to switch OS's to Mint or PCLOS, but i would really love to keep my files, and ubuntu, hopefully.

---

### Post by mmsmc on 2011-03-05
where did you download it to?

---

### Post by Hedgehog1 on 2011-03-06
> **Haylinux said:**
> I went to mount the third .ISO for installation, and BAM! my computer froze, so i waited five minutes, came back, and still frozen. **_shut it down for 20_** minutes, pulled it back up, and it's got this error as follows;
"Mount: mounting /dev/disk/by-uuid/65b0a6a-a366-435a-a086-58428cfe2bd1 on /root

Haylinux,

I think the shutdown with unwritten data set this situation up.

We need to get a look at your disk partition layout.

Please boot off of an Ubuntu LiveCD, select the 'TRY' option, then:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

---

### Post by Haylinux on 2011-03-06
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00002fe7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18693   150145024   83  Linux
/dev/sda2           18693       19458     6142977    5  Extended
/dev/sda5           18693       19458     6142976   82  Linux swap / Solaris
ubuntu@ubuntu:~$ a2           18693       19458     6142977    5  Extended
a2: command not found
ubuntu@ubuntu:~$ /dev/sda5           18693       19458     6142976   82  Linux swap / Solaris
bash: /dev/sda5: Permission denied

---

### Post by oldos2er on 2011-03-06
While you're booted from the LiveCD, run **sudo fsck sda1** (make sure sda1 is not mounted), then try rebooting into Ubuntu.

---

### Post by Haylinux on 2011-03-06
it said ''command not found''
And then, after another try:
"fsck from util-linux-ng 2.17.2"

---

### Post by oldos2er on 2011-03-07
Did you copy and paste the command I gave you? It would help to see the entire terminal output too.

---

