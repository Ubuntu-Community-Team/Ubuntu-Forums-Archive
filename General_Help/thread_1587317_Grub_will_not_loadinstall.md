---
title: "Grub will not load/install"
date: 2010-10-03
forum: General Help
---

### Post by pilotguy415 on 2010-10-03
I had some issues after installing Ubuntu with Windows 7 and not being able to load windows after the install. Well, I got that fixed and Windows 7 installs fine. To prevent losing data I repartitioned my hdd and set everything up to have multiple backups and run windows/linux on the same drive on two separate partitions. 

Anyway, installing linux went find. I installed windows, that went fine too. I tried booting into linux and Grub does not load at all. I then installed EasyBCD on windows and set up the ubuntu boot option and still cant get linux to boot. It gives me different error messages. I removed the EasyBCD boot options and decided to try and load Grub again. So I booted from a Live CD and opened terminal. Following steps in the Wiki this is what I did: 

> ubuntu@ubuntu:~$ mount | tail -1
/dev/sdb2 on /media/57225255-990e-4604-a006-7e2ed266c232 type ext4 (rw,nosuid,nodev,uhelper=udisks)
ubuntu@ubuntu:~$ ls /media/57225255-990e-4604-a006-7e2ed266c232/boot
abi-2.6.32-24-generic         memtest86+.bin
config-2.6.32-24-generic      System.map-2.6.32-24-generic
grub                          vmcoreinfo-2.6.32-24-generic
initrd.img-2.6.32-24-generic  vmlinuz-2.6.32-24-generic
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/57225255-990e-4604-a006-7e2ed266c232 /dev/sdb2
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
So I'm concerned with Grub trying to install on a partition and not the MBR.

I tried to update Grub to see if that would solve anything and I get this:
> ubuntu@ubuntu:~$ sudo update-grub2
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
I am completely lost as to what I should do at this point. Any help is greatly appreciated. Oh, if it helps, here is the fdisk for my hdd running Ubuntu and Windows 7

> Disk /dev/sdb: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00098a3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2         271     2041169+   f  W95 Ext'd (LBA)
/dev/sdb2             272        7764    56647080   83  Linux
/dev/sdb3   *        7765        7778      102400    7  HPFS/NTFS
/dev/sdb4            7778       15506    58419200    7  HPFS/NTFS
/dev/sdb5               2         271     2041168+  82  Linux swap / Solaris


---

### Post by oldfred on 2010-10-03
Your install line said to install to sdb2 which is the partition, did you not mean to say sdb which is the MBR of the sdb drive. Then you can set BIOS to boot sdb and grub should load.

You should not have to use UUIDs:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

Install MBR from LiveCD, Ubuntu install on sdb2 and want grub2 in drive sdb's MBR:
Find linux partition, change sdb2 if not correct, and/or even sdb if sda wanted:
sudo fdisk -l
sudo mount /dev/sdb2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb

---

### Post by pilotguy415 on 2010-10-05
Thank you! That is what I was doing wrong. Using the commands you listed worked perfectly and now I can smoothly dual boot windows and linux again!

---

