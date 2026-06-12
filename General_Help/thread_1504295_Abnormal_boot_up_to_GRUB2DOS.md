---
title: "Abnormal boot up to GRUB2DOS"
date: 2010-06-07
forum: General Help
---

### Post by sauwen on 2010-06-07
Hi and help!

This all started when I finished doing some updates via the update manager.  I was asked to restart, but for some reason, only text was displayed on the screen.  Thus.. I did a hard shutdown. When I rebooted, I only get a prompt with this shown:

GRUB2DOS 0.4.4 2009-04-20, Memory: 636K / 2045M, MenuEnd: 0x4349E
[Minimal BASH-like line editing is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists the possible completions of a device/filename.  ESC at any time exits.]

Typing in 'boot' gives me 'Error 8: Kernel must be loaded before booting'.

Doing 'grub> find /boot/grub/stage1' shows me that it doesn't exist.  I was following this page: [http://ubuntuforums.org/showthread.php?t=922678](http://ubuntuforums.org/showthread.php?t=922678) and got to where I could use a terminal in the desktop for beginning ubuntu users when I boot from the ubuntu live CD. Is this the right terminal?  Or is this terminal giving me the wrong answer?  I did 'sudo fdisk -l' and it shows:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/0 size (minimum/optimum): 512 bytes / 512 bytes
Disk identifier: 0x40b22384

Device   Boot     Start     End     Blocks     Id     System
/dev/sda1           1      14     112423+     de    Dell Utility
/dev/sda2 *         15     19457  156175897+  7     HPFS/NTFS

Where's my linux partition?

Should I just reformat my linux partition?  It looks like it is gone forever.  :(

Thank you in advance for any insight you folks can give me.

---

### Post by Serpher on 2010-06-07
Did you install through wubi? If so your Linux partition is the NTFS partition and doesn't work the same as an actual full Linux install.

---

### Post by sauwen on 2010-06-09
Supposedly so, since ubuntu was installed on a computer with Windows on it already for dual boot.  Any recommendations?  Or should I just do a reinstall using the ubuntu live CD?
 
Thanks.

---

### Post by sauwen on 2010-06-09
I also tried doing these commands in GRUB:
 
grub> root hd(0,1)
grub> kernel /boot/ <tab>
and it does not show me any list of kernels...  :(  
 
I tried the other partition and the same thing happened.

---

