---
title: "trying to reinstall windows"
date: 2006-02-07
forum: General Help
---

### Post by angeleyes on 2006-02-07
:( 
ok heres the deal --
I like Ubuntu but hubby and kids like Windows-I want to make it permenant dual boot system.I dont have  a XP disk so I want to go back to Me(which we liked better anyway)I ran fdisk from my ME boot disk and now my fdisk on Ubuntu looks like this:
Disk /dev/hda: 80.0 GB, 80060424192 bytes
240 heads, 63 sectors/track, 10341 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         575     4346968+  83  Linux
/dev/hda2   *         576         852     2094120    6  FAT16
/dev/hda3           10341       10341        7560   82  Linux swap / Solaris
I have tried to run my ME install disk but it wont run.
Can anyone help me ??
I appreciate any help.

---

### Post by angeleyes on 2006-02-07
hmm ran fstab from terminal and this is how it looks:

#/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2      /windows ntfs nls=utf8,umask=0222 0 0
/dev/hda3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by rock freak on 2006-02-07
so what are you trying to do?? 

reinstall windows ME as well as ubuntu so you can load both from grub ????

---

### Post by skirkpatrick on 2006-02-07
ME will want to install (I think) to the first partition of the first drive.

---

### Post by angeleyes on 2006-02-07
I want to be able to dual boot my system.

---

### Post by angeleyes on 2006-02-07
[QUOTE=skirkpatrick]ME will want to install (I think) to the first partition of the first drive.[/QUOTE]
ok ...can you tell me how to get it to run my ME install disk?

---

### Post by Iowan on 2006-02-07
I'm perpetually wrong (hope so, in this case), but I suspect you may have to re-install ME, then fix the damage to GRUB.  Might be easier to get a new husband and kids. :mrgreen:

The install disk (floppy?) SHOULD boot.  Is the BIOS set to boot from floppy before HD?

---

### Post by z_diver on 2006-02-07
If you install ME first the basic installation should wipe the drive(or at least the first partion) and leave you with a running ME system.  Then install Ubuntu afterwards so Ubuntu will see the ME install on Fat32 and partition the drive for dual boot.  Of course if your ME installer won't run I don't know how you intend to install ME anyway.  It runs in RAM so it should not stop running due to partitions.

---

### Post by skirkpatrick on 2006-02-07
I really think that I'd save off any important Ubuntu documents, settings, downloaded programs, etc. and burn it to a CD.  Boot a Live CD and use gparted to wipe all the partitions.  Install ME and make sure it's happy then install Ubuntu.  It's stuff like this that makes me thankful for dual-booting from two drives, especially after I found out how to make the Linux drive the first drive and fool Windows into being on the 2nd drive so it doesn't mess up my MBR.

It really does sound like your ME CD may have problems.  When you say it doesn't install, what does it complain about?

---

### Post by angeleyes on 2006-02-07
[QUOTE=skirkpatrick]I really think that I'd save off any important Ubuntu documents, settings, downloaded programs, etc. and burn it to a CD.  Boot a Live CD and use gparted to wipe all the partitions.  Install ME and make sure it's happy then install Ubuntu.  It's stuff like this that makes me thankful for dual-booting from two drives, especially after I found out how to make the Linux drive the first drive and fool Windows into being on the 2nd drive so it doesn't mess up my MBR.

It really does sound like your ME CD may have problems.  When you say it doesn't install, what does it complain about?[/QUOTE]
I tried to run the CD after loading Ubuntu  and the Me disk will bring up the screen to browse the disk etc.-I can get setup to start but then in 2 seconds it disappears.
I did notice that even though I deleted the Windows partion using Gparted the XP version still appears as the choose OS screen on boot up.

---

### Post by rawkasaurus on 2006-02-07
I tried to install XP after I installed Ubuntu and it said that there was a partition (although it was on a separate physical drive) that was not compatible with Windows and so it couldn't install Windows.  I don't know if this will happen with ME but just a bit of info that might be good to know after taking so long to figure out your problem and then not being able to install ME.

---

### Post by lifeperfecti0n on 2006-02-07
I am using dual boot with Ubuntu and XP. I have faced problems similar to yours when I tried to install Win 98. The problem is that ME does not know how to overwrite the Linux MBR, and it won't be able to boot anyway even if it installs. The installer probably stops at this point. I suggest that you make a backup of your system, use a good partition manager (not the Linux one cause partition tables made by it are often not recognised by Windows) such as fdisk or Partition Magic to make fat32 file systems. Leave some free unpartitioned space and install ME in the fat32 partition. Now install Ubuntu after making ext3/reiserfs filesystem in the unpartitioned space. The Ubuntu setup is quite helpful and I'm sure you won't have much problems.
Good luck!

---

### Post by skirkpatrick on 2006-02-07
[QUOTE=angeleyes]I tried to run the CD after loading Ubuntu  and the Me disk will bring up the screen to browse the disk etc.-I can get setup to start but then in 2 seconds it disappears.
I did notice that even though I deleted the Windows partion using Gparted the XP version still appears as the choose OS screen on boot up.[/QUOTE]

Using Gparted to blow away a partition only blows away the partition.  To remove the option in the boot screen, edit **/boot/grub/menu.lst**.

I'm still willing to bet that ME wants to install on the first partition, hda1, which is not available.  I hated ME as soon as I purchased it.  It lasted about 6 weeks then I went back to 98se.

---

### Post by angeleyes on 2006-02-07
[QUOTE=skirkpatrick]I really think that I'd save off any important Ubuntu documents, settings, downloaded programs, etc. and burn it to a CD.  Boot a Live CD and use gparted to wipe all the partitions.  Install ME and make sure it's happy then install Ubuntu.  It's stuff like this that makes me thankful for dual-booting from two drives, especially after I found out how to make the Linux drive the first drive and fool Windows into being on the 2nd drive so it doesn't mess up my MBR.
:confused: 
It really does sound like your ME CD may have problems.  When you say it doesn't install, what does it complain about?[/QUOTE]
is  there any way you can give me steps in how to do it and Install ME ?
Im new to this and dont want to end up with nothing but a blank computer?
I would really really appreciate it if anyone could

---

### Post by angeleyes on 2006-02-07
heres some added info when I ran fdisk in the terminal this is what it reads:

Disk /dev/hda: 80.0 GB, 80060424192 bytes
240 heads, 63 sectors/track, 10341 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         575     4346968+  83  Linux
/dev/hda2   *         576       10340    73823400   83  Linux
/dev/hda3           10341       10341        7560   82  Linux swap / Solaris

does this help any?

---

### Post by skirkpatrick on 2006-02-08
Well, as stated earlier, I'd save off anything that you want to keep from Ubuntu onto a CD, floppy, or USB drive because you are going have a blank machine at some point.

1) Bootup using the Live CD and use Gparted to delete all your partitions.

2) Bootup with the ME install CD.  When it wants to size a partition, only give it how much space you want.

3) When ME is completely happy, including performing all Windows updates, bootup the Ubuntu install CD.

4) Follow Ubuntu's normal installation process and restore any data that you had saved off.

---

### Post by angeleyes on 2006-02-08
[QUOTE=skirkpatrick]Well, as stated earlier, I'd save off anything that you want to keep from Ubuntu onto a CD, floppy, or USB drive because you are going have a blank machine at some point.

1) Bootup using the Live CD and use Gparted to delete all your partitions.

2) Bootup with the ME install CD.  When it wants to size a partition, only give it how much space you want.

3) When ME is completely happy, including performing all Windows updates, bootup the Ubuntu install CD.

4) Follow Ubuntu's normal installation process and restore any data that you had saved off.[/QUOTE]
ok thanks . my ME install disk should work with no OS on the computer?

---

### Post by angeleyes on 2006-02-08
[QUOTE=skirkpatrick]Well, as stated earlier, I'd save off anything that you want to keep from Ubuntu onto a CD, floppy, or USB drive because you are going have a blank machine at some point.

1) Bootup using the Live CD and use Gparted to delete all your partitions.

2) Bootup with the ME install CD.  When it wants to size a partition, only give it how much space you want.

3) When ME is completely happy, including performing all Windows updates, bootup the Ubuntu install CD.

4) Follow Ubuntu's normal installation process and restore any data that you had saved off.[/QUOTE]
ok thanks . my ME install disk should work with no OS on the computer?

one other question --how much space do you think ME will want?I have no clue and dont want to give it too little.

---

### Post by ssstrx on 2006-02-08
poor thing i wouldnt wish ME on my worst enemy

---

### Post by angeleyes on 2006-02-08
cant use my ME disk anyway...its the upgrade and I dont have any other Windows OS disk to use to verify that I get the upgrade so back to square 1 ..
looking at just buying the XP version ---but ouch thats gonna be spendy..

---

### Post by skirkpatrick on 2006-02-08
Ouch, better to make them use Linux :)


You might be able to find somebody that'll give you a 98se disc.  I've changed two of the computers in my home back to 98se from XP due to problems with the games they wanted run.

---

### Post by Nemisisfate on 2006-11-03
now i have a small problem here. i want to reinstall my windows XP on the system but i don't have a disk. would a computer from at least 3 or 4 years ago have the capability to reinstall the OS when the computer starts up? or will i have to get an XP disk? my laptop has that capability. of course i want to make this computer a dual boot system. do i have to delete Ubuntu? if so i have already made a back-up of all my files and a new ubuntu install. a quick reply would be appreciated.

---

