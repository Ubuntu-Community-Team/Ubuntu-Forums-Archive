---
title: "UNR won't boot"
date: 2010-02-19
forum: General Help
---

### Post by fat_tail_rider on 2010-02-19
My Atom processor desktop has suddenly stopped booting UNR. On boot, I get a menu allowing me to boot to several Ubuntu Linux versions or their recovery modes. Booting to the recovery mode, I eventually get the message "Gave up waiting for the root file system."

Weird thing is, I have run a test of the hard drive and memory from my flash drive backup system and both have run and passed. But when I try either to run UNR without changing the installed system or re-install it, the system hangs up, just as it does when I try to boot from the hard drive.

I assume this is a hardware problem, but on the chance it's not, any ideas on fixes?

Thanks!

---

### Post by quixote on 2010-02-21
Is it possible the grub entry was somehow corrupted and is no longer pointing to the right partition to be able to find your UNR root filesystem?  What is the organization of your harddrive?  For instance, copy the output of ```
sudo fdisk -l      *("l" as in "list")*
``` to your answer.  (You can select it with the mouse in the terminal window, and then hit ctrl-**shift**-c to copy it it.  Paste into the forum with the usual ctrl-v.)  

Are you using UNR karmic, ie grub2?  I'm going to have to check how to see what it's doing, I'm not very familiar with it.  Lots of info on grub2 here: [http://ubuntuforums.org/showthread.php?p=8191211#post8191211](http://ubuntuforums.org/showthread.php?p=8191211#post8191211) and here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by fat_tail_rider on 2010-02-21
Thanks, quixote. I believe the problem was in fact a corrupted grub file. This was my first UNR install from the 9.10 ISO; the other two were from the 9.04 IMG file, which were then upgraded online to 9.10.

When I could not get 9.10 on the flash drive I had used for the install to boot the demo installation on my working netbook, I used USB Startup Disk Creator to create a new bootable flash. When that booted normally to the demo OS, I went ahead and installed it. (This is my mother's computer, used exclusively for Web browsing and email, so I all I had to do was restore the address book and bookmarks.) Everything now seems to be working fine.

For what it's worth, here's the fdisk output:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6b4800d6

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19086   153308263+  83  Linux
/dev/sda2           19087       19457     2980057+   5  Extended
/dev/sda5           19087       19457     2980026   82  Linux swap / Solaris 

I suppose there is still an outside chance the grub file was installed on a failing sector . . .

wayne

---

### Post by quixote on 2010-02-21
Sounds like the problem has gone away with a reinstall.  Excellent!  Honestly, three quarters of the time the simplest thing -- if you can do it -- is just to reinstall the whole kit and caboodle. 8-)

---

