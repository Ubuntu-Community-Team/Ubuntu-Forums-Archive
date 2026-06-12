---
title: "USB Dual boot - How to setup"
date: 2012-01-23
forum: General Help
---

### Post by airscrew on 2012-01-23
**USB Dual boot - How to setup**             
                                                                Hi to all,

Newbie to Ubuntu here.
Installed 11.10 on my sons laptop when windows died. 
No probs, and he loves it.

How do I install Ubuntu as a dual-boot for my desktop.??
I am most of the way through it, but I need to know how/where to install grub.
I have scoured this forum, and gone as far as I can with the install, as none of the discussions exactly fits my requirement.

NB. I use it partly as a homeoffice desktop, and I do NOT want to touch  the C: drive at all. Although I have an XP disk, it would take AGES to  rebuild a 5 year old image...if it aint broken...you know the rest.

Disk/boot config is:

drive 0(a): NTFS 250Gb
C: windows XP SP3 and old progs - 50Gb
D: all data and new progs since I repartitioned and set a weekly D: backup regime - 200Gb

drive 1(b): USB drive 500Gb NTFS
recently changed partitions (gpart) to
W: (as windows sees it)  1st partition. Gpart sees free space 250Gb with 11.10 installed, but NOT bootable YET
X: 100Gb data backup for D:
Z: 50Gb Windows image backup (used DriveImageXML) I DO NOT WANT TO LOOSE THIS IMAGE, and dont have another drive

11.10 installed OK, good iso and chksum, but not bootable


OK, so here is the question.
IDEALLY, I would like to boot into Ubuntu if/when the USB drive is powered.
Heres my thinking.
Bios is <now> set to boot first to CD, then to USB drive (currently no MBR or grub), then to drive 0 normal XP.
If no CD and no USB, it will autoboot to XP.
This works in BIOS. 
OK sofar.

Qs. 
So will this work if grub is installed as Ubuntu only (not dual), and sitting on the USB drive?
Will I have to disconnect (cables) the XP drive to force grub to install  onto the USB drive? (i would prefer to do this to ensure I do not touch  the XP drive)
Will this cause a drive conflict after I reconnect the XP drive?
Will Ubuntu be able to fully access the data on D:???:

NB.
I have a valid liveCD, and a bootable GpartEd CD
I would strongly prefer to do this totally with the XP drive disconnected.
I would really prefer this to happen during the install process.
I dont want to have to do a load of terminal script post install. I will get it wrong!!
Also, I expect to have re-do the install process, and enticipate  reducing the freespace for Ubuntu down from 250Gb to (say) 25B, and  free/keep more space for backups in another partition.

Thanks for any and all advice.
Jai.

---

### Post by oldfred on 2012-01-23
Many suggest disconnecting drives to make sure you only install to the drive you intend to. If ok with doing that it can be the safest way.

You should have good backups as any partitioning changes can cause data issues. Some have power failures, children, pets, other disconnecting something, all sorts of issues. Backup is always safest.

But I prefer to manually partition in advance.  It sounds like you understand partitions. Then with manual install you get a combo box on the partition screen on where to install the grub2 boot loader. Just be sure to choose the USB drive.

Since most of your data will be in shared NTFS partitions you do not have to have a separate /home. The separate /home makes it easier to reinstall. But /home has two purposes. It has all the (hidden) user settings and files and all your data. If data is elsewhere /home is small and easily backed up.

Install to external drive 11.04.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

If necessary you can reinstall the XP boot loader to the internal drive.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

My standard recommendation.
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by dragonfly41 on 2012-01-23
Just to add a further option for consideration  ..

try unetbootin installed in windows to create ubuntu in your external USB drive ..

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

When booting up hit F12 and choose USB for ubuntu boot.

---

### Post by oldfred on 2012-01-23
CAUTION.
dragonfly41's instructions are fine for a USB flash drive. But if you do that to a large hard drive, you may erase entire drive.

The flash drive installers normally erase entire drive and create a FAT32 partition for the installer. Which is the normal case for a 1 or 2GB flash drive.

---

### Post by dragonfly41 on 2012-01-23
OldFred

I'll note that warning ... but I was fairly sure that I've used unetbootin to burn to a larger drive.  I'll check that out.

I have a dual boot Vista + Ubuntu-10.10 on my laptop .. and on an external drive in an enclosure  I have Edubuntu-10.10.

---

### Post by airscrew on 2012-01-24
Thanks Fred, that looks pretty clear. I will try it tonight.

---

