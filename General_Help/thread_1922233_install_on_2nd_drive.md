---
title: "install on 2nd drive"
date: 2012-02-08
forum: General Help
---

### Post by Nihilithik on 2012-02-08
i have 2 500g hard drives installed on m pc now. i was wondering if i can install ubuntu on one, and keep win7 on the other. i know win7 doesnt allow dual boot anymore, but if i install ubuntu on the drive that doesnt have win7 loaded on it, will it work?

also, if i am able to have the 2 installed, will i be able to get to files on both drives while in ubuntu?

---

### Post by jamesisin on 2012-02-08
I was able to build a dual-boot system with Windows 7 and Ubuntu 10.04 (actually triple including XP) and use Grub to manage the three installations.  Here is my article on the process:

[http://jamesisin.com/a_high-tech_blech/index.php/2012/01/repairing-grub-after-windows-breaks-it/](http://jamesisin.com/a_high-tech_blech/index.php/2012/01/repairing-grub-after-windows-breaks-it/)

---

### Post by oldfred on 2012-02-08
You want to be sure to use manual install so you get the option on where to install the grub2 boot loader. You want it on the Ubuntu drive not the Windows drive. Some suggest disconnecting the Windows drive, which works, but with manual install you get a combo box that lists drives (and partitions which you do not use) on where to install the boot loader.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

Ubuntu will see the Windows NTFS partitions, but Windows will not see the Linux formated partitions. Often best to set Windows as read only in Ubuntu to avoid accidental damage and use a shared NTFS partition for any data you may want in either system. I put my Firefox & Thunderbird profiles in the shared NTFS partition.

---

### Post by leclerc65 on 2012-02-08
My dual boot scheme is as follow:
1- Install XP on SDA
2- Install Ubuntu (actually Lubuntu) on SDB, with Grub on SDB (while installing, click 'Advanced')
3- Change boot hard drive priority to SDB

If I need XP, I hit Escape, or in case I miss it , just wait for the Grub screen to appear. SDA is a very old 20G Maxtor that can fail anytime, but I created a NTFS partition on SDB to be shared by both Windows and Linux.

---

### Post by collisionystm on 2012-02-08
> **Nihilithik said:**
> i have 2 500g hard drives installed on m pc now. i was wondering if i can install ubuntu on one, and keep win7 on the other. i know win7 doesnt allow dual boot anymore, but if i install ubuntu on the drive that doesnt have win7 loaded on it, will it work?

also, if i am able to have the 2 installed, will i be able to get to files on both drives while in ubuntu?


Easy.

Just install ubuntu with your windows drive unplugged

afterwards hook it back up, boot ubuntu and run update grub

---

### Post by Nihilithik on 2012-02-08
Thanks for all the help everyone. I just had one more question, i've had ubuntu since JJ, and have been learning as much Linux as i need, as i needed it. 
Being able to share files between both OS, and creating a NTSF partition that i can use to do that. Can i get a little help on that, so i dont hurt anything by sudo'n code i have no idea it's doing?

---

### Post by jamesisin on 2012-02-08
The Ubu install ought to be able to mount the NTFS partition you have for Windows 7 if you need to access files directly.  Otherwise you could create a sharing partition (in either FAT32 or NTFS) and both systems would be able to access that as well.

I use gparted (it's in the repositories) to move and resize partitions.  Since partitions must be unmounted to be resized you may have to use the live CD if you ever need to resize your existing Ubu partition (gparted is included in the live CD).

Just proceed with caution.

---

### Post by oldfred on 2012-02-08
Some info on shared NTFS partitions.

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by Nihilithik on 2012-02-08
Thanks for all the help. Now the long process of backing up files onto netbook, just in case i frag something. I'll post back when I have indeed created my work around win 7 no dual boot, dual boot pc.

---

