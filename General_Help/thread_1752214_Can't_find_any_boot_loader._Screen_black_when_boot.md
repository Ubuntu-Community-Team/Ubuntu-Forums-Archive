---
title: "Can't find any boot loader. Screen black when booting"
date: 2011-05-07
forum: General Help
---

### Post by airborne2k10 on 2011-05-07
Hello. I recently installed Win 7 in a 4 partition hardrive. sda1 was some recovery partition. sda2 said "System Reserved". sda3 was my ext4 ubuntu partition. sda4 was my win7 partition. When I installed win7 I could only boot to win7 so I got onto ubuntu's tut for recovering grub and I attempted to recover it and I think I failed. When I boot I just go to a black screen. I since then deleted my sda1  & sda2 partitions (I really hope system reserved was not needed.) I'm still not 100% sure how the bios knows to boot straight to grub when it boots. What is the first thing on the hard drive that a bios looks for?? Anyways, the only access I have to a functioning comp is through a 10.04 live cd. Could you help me learn about booting and help me to get grub back up and running. Thankyou

---

### Post by Hedgehog1 on 2011-05-08
Windows 7 typically uses 2 partitions:

1) Small 'system reserved' partition to boot
2) ntfs partition that is really Windows 7.

I think your best plan of attack is to backup your data, and then reinstall Windows 7 first, then then reinstall Ubuntu.

Your goal is to have a partition layout that looks like this:

[B]/dev/sda1 NTFS System reserved (Created by Windows 7 install)
/dev/sda2 NTFS Windows 7 (Created by Windows 7 install)
/dev/sda3 NTFS Common shared data area, used by Windows and Ubuntu
/dev/sda4 Extended Partition
__/dev/sda5 ext4 Ubuntu '/' (root) partition
__/dev/sda6 ext4 Ubuntu '/home' partition
__/dev/sda7 Swap (Size of your RAM plus 10%)[/B]

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-08
**Here is an example of installing an newer Ubuntu from the LiveCD/LiveUSB with a separate '/home' partitions.**

[IMG]http://img27.imageshack.us/img27/6770/03allocdrivespace1.png[/IMG]

First, make /dev/sda5 your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Next, set up the swap partition.  This usually sets itself up just fine, but double check it.

[IMG]http://img263.imageshack.us/img263/7656/06allocdrivespace4.png[/IMG]

The last partition to setup is the '/home' one:

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

This brings you to here:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

[SIZE="4"]**Please install the Boot Loader on /dev/sda !**[/SIZE]

Press "Install Now" and you are on your way:

[IMG]http://img855.imageshack.us/img855/7153/09installbegin.png[/IMG]


**This will give you a clean dual boot install, you just need to restore your data**


***The Hedge***

---

