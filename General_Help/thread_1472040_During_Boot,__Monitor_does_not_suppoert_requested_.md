---
title: "During Boot,  Monitor does not suppoert requested resolution"
date: 2010-05-04
forum: General Help
---

### Post by rodh on 2010-05-04
Just did the upgrade to 10.04,  During boot I get lines and random numbers/letters in varied colors,  After login screen appears and I log in, during the splash screen display a small info window appears in upper right corner says "Monitor does not support resolution requested.  After my desktop comes up everything seems fine and I check the resolution and it is set to the monitor defaults.  When I go look at x-org I find that both upgrade files have been backed up and the system is using my x.org-config from 7.10.  Everything seems to be working fine at this time.  But every boot up is the same. And I am unable to locate the file that is requesting a higher or lower resolution (/ect/default/grub) is empty and that is the only place I have found that even mentions boot up resolution problems.  Any ideas, leads to a fix would be greatly appreciated.:)  By the way I am happy with 10.04 so far and Firefox is faster then it ever has been on this old machine Build 98'  Upgraded 2003  and I don't remember what all I did,  ASUS k8-mx motherboard with on board graphics, AMD Sempron CPU - HP w2007 Wide screen monitor supports 1680x1050 res

---

### Post by rodh on 2010-05-04
just adding some attachments that might be of some help,

---

### Post by rodh on 2010-05-04
Files that might help;

rod@rod-desktop:~$ sudo fdisk -l
[sudo] password for rod: 

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000900cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30515   245111706   83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c96ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       38428       38913     3903795   82  Linux swap / Solaris
/dev/sdb2               1       38427   308664846    5  Extended
/dev/sdb5               1       18665   149926549+  83  Linux
/dev/sdb6           18666       37732   153155646   83  Linux
/dev/sdb7           37733       38427     5582556   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 16.0 GB, 16026435072 bytes
64 heads, 32 sectors/track, 15283 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00002220

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       15283    15649776    c  W95 FAT32 (LBA)
rod@rod-desktop:~$ 

----------------------------------------------------------------------------------------------------------------------------------------------

rod@rod-desktop:~$ sudo blkid
/dev/sda1: UUID="5b5a6c51-edae-4266-88c6-c89ea2e3f736" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="01e58d99-066e-462a-a663-e2842a14383b" TYPE="swap" 
/dev/sdb5: UUID="ae5d4997-4763-473e-89fa-50f1eb72bf30" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="3d10019e-9068-4fd7-b72f-47dfea048e95" TYPE="ext3" 
/dev/sdb7: UUID="2d1d476e-e631-4dfb-8d88-c4899756651c" TYPE="swap" 
/dev/sdc1: LABEL="BACKUP THUM" UUID="97C1-D002" TYPE="vfat" 
rod@rod-desktop:~$

---

### Post by jschille on 2010-05-04
I had the same problem.  Check out my thread and follow that guy's directions.

[http://ubuntuforums.org/showthread.php?t=1471927](http://ubuntuforums.org/showthread.php?t=1471927)

Ill copy and paste what he sent me.

> **GSF1200S said:**
> 

Enter the following commands in a terminal:
```
sudo apt-get remove grub
sudo apt-get install grub-pc
sudo grub-install /dev/sda
sudo update-grub2
```After running that last command, you should see  your linux and windows install listed in the terminal output. Next, we  try to fix your splash problem (and hopefully it speeds up your boot):
```
sudo apt-get install v86d
gksu gedit /etc/default/grub
```

Look for the line that says:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 			 		
and replace it with:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset  video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap" 			 		

Then, look for the line that says:
#GRUB_GFXMODE=640x480 			 		
and replace it with:
GRUB_GFXMODE=1280x1024 			 		
Save the file and exit gedit.

Next, run the following command:
```
gksu gedit /etc/initramfs-tools/modules
```and add this line at  the end of the file:
```
uvesafb mode_option=1280x1024-24 mtrr=3 scroll=ywrap
```Save  the file and close gedit.

Then, run this command in a terminal:
```
echo FRAMEBUFFER=y | sudo tee  /etc/initramfs-tools/conf.d/splash
```Finally, run the following two  commands:
```
sudo update-grub2
sudo update-initramfs -u
```The above worked for me on an Nvidia  9800GTX.

---

### Post by Lostsouls on 2010-05-04
I have sort of the same problem, working with a 15,4 inch monitor on a machine, after half boot ( the line blinking in the left corner ) it says, signal out of range and goes black. When i connect a 15 inch CRT after booting it stays black BUT if i boot with the CRT it boots fine, after login i can connect the 15 inch lcd and it stays online till the next reboot..

---

### Post by rodh on 2010-05-04
I haven't had a CRT monitor for years,  I am glad you had one to try.

---

### Post by Lostsouls on 2010-05-04
Well i just found out, it won't boot with the 15 inch LCD, at all... doesn't even load the splash screen of Ubuntu. Quite strange this PC won't boot with an LCD ? but will with a CRT xD Any recommendations ?

---

### Post by rodh on 2010-05-05
OK, that Didn't work, worked for the boot resolution problem but only twice,  the boot is still slow,  But not to bad.  Now I am chainloading grub - grub2 and in grub legacy it say's to run command: [upgrade-from-grub-legacy].  I tried running the command in grub, and in grub2, [Not a valid command] does anyone know where I am suppose to run that command,  I also tried in terminal.

---

### Post by rodh on 2010-05-05
Bump

---

