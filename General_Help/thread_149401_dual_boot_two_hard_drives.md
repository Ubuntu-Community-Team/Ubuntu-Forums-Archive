---
title: "dual boot two hard drives"
date: 2006-03-23
forum: General Help
---

### Post by wbsquared on 2006-03-23
I have two hard drives. The master being 40GB and the slave 120 GB.

Im planning on dual booting my computer. One OS XP the other Ubuntu 5.10.  Since im new to Linux (all distros) im wondering if installing Ubuntu beside XP on my master hard drive, will Ubuntu still detect my slave hard drive if I am in the Ubuntu environment?

Thanks

---

### Post by taurus on 2006-03-23
It should without any problem.  Make sure you install GRUB on MBR so you can boot either Ubuntu or XP.  If Ubuntu doesn't mount your /dev/hdb1 (second harddrive) automatically, then you just add one line to your /etc/fstab and you're done.  :)

---

### Post by nife on 2006-03-23
I just did it and ubuntu recognized my windows xp install with no problems and even created the grub settings for it.  Easy as pie.

---

### Post by wbsquared on 2006-03-24
I have the dual boot working, but ubuntu is not seeing my other hard drive which has been formatted in ntfs, and was never touched during the installation.

C: drive (40GB) -- contains both XP and Ubuntu 5.10

D: drive (120GB) -- contains misc files

Is there a way to access the D: drive through Ubuntu?

---

### Post by pooler on 2006-03-24
[QUOTE=wbsquared]I have the dual boot working, but ubuntu is not seeing my other hard drive which has been formatted in ntfs, and was never touched during the installation.

C: drive (40GB) -- contains both XP and Ubuntu 5.10

D: drive (120GB) -- contains misc files

Is there a way to access the D: drive through Ubuntu?[/QUOTE]

Yep, add this line to /etc/fstab (must be done as root):

```
/dev/hdb1 /media/misc ntfs readonly 0 0
```

Then execute this commands (as root):
```
mkdir /media/ntfs (this creates the mount point)
mount /media/ntfs (only the first time, it should be mounted after you boot Ubuntu)
```.
To see the files of that disk, you would point Nautilus/Konqueror/whatever to /media/ntfs
Note that currently linux doesn't have 100% native foolprof write support, but you might want to try captive-ntfs (google it for info). Also, the partition might not be /dev/hdb1 (altrought it is 99% likely that it is). If it doesn't work, type (as root) ```
sfdisk -l /dev/hdb
``` to see all the partitions of that disk.

---

### Post by wbsquared on 2006-03-24
To sound more like a noob (which i am to linux) could i get a slightly more detailed explaination of what you said.

For example i don't see fstab in the /etc folder when i go through the filesystem.

Its greatly appreciated

---

### Post by Mustard on 2006-03-24
[QUOTE=wbsquared]To sound more like a noob (which i am to linux) could i get a slightly more detailed explaination of what you said.

For example i don't see fstab in the /etc folder when i go through the filesystem.

Its greatly appreciated[/QUOTE]

If you don't see the fstab file in the /etc/ folder then that is quite a strange occurence. It's pretty much guaranteed that it would be there. The fstab file is where all the mount points are configured for startup, so its pretty fundamental to the operating sytem.

Have you worked out how to get to a command line yet, using the Applications>>Accessories>>Terminal menu option?

---

### Post by wbsquared on 2006-03-24
[QUOTE=Mustard]If you don't see the fstab file in the /etc/ folder then that is quite a strange occurence. It's pretty much guaranteed that it would be there. The fstab file is where all the mount points are configured for startup, so its pretty fundamental to the operating sytem.

Have you worked out how to get to a command line yet, using the Applications>>Accessories>>Terminal menu option?[/QUOTE]

I figured out the command line, i use some of that in my openGL class i have here.  Though im still not that great at using it.

---

### Post by wbsquared on 2006-03-24
I looked up more info on google about /etc/fstab and apparently people that do not have this file when they reboot, Linux itself will not boot.  So i attempted rebooting Linux and it booted normally.

Should i reinstall Ubuntu and hope in installs that the /etc/fstab file?
or could the problem be that when i installed Ubuntu i had the following:
partition 1 -WinXP (15GB) (ntfs)
partition 2 -Linux (Ext 3) (about 15 GB)
partition 3 -Linux (swap) 
partition 4- Logical (10GB Fat32)

or does that look ok?

Any ideas would be extremely appreciated.

---

### Post by Mustard on 2006-03-24
[QUOTE=wbsquared]I looked up more info on google about /etc/fstab and apparently people that do not have this file when they reboot, Linux itself will not boot.  So i attempted rebooting Linux and it booted normally.

Should i reinstall Ubuntu and hope in installs that the /etc/fstab file?
or could the problem be that when i installed Ubuntu i had the following:
partition 1 -WinXP (15GB) (ntfs)
partition 2 -Linux (Ext 3) (about 15 GB)
partition 3 -Linux (swap) 
partition 4- Logical (10GB Fat32)

or does that look ok?

Any ideas would be extremely appreciated.[/QUOTE]

Your line of reasoning is failing here. :)

no /etc/fstab means no boot, so you boot successfully, hence you have an /etc/fstab file.  The problem is you can't find it.  It is there though.  I think the answer is to look harder for the /etc/fstab file.

Try this command in terminal

```
cat /etc/fstab
```

What do you see?

---

### Post by wbsquared on 2006-03-24
[QUOTE=Mustard]Your line of reasoning is failing here. :)

no /etc/fstab means no boot, so you boot successfully, hence you have an /etc/fstab file.  The problem is you can't find it.  It is there though.  I think the answer is to look harder for the /etc/fstab file.

Try this command in terminal

```
cat /etc/fstab
```

What do you see?[/QUOTE]

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

```

---

### Post by Mustard on 2006-03-25
[QUOTE=wbsquared]```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

```[/QUOTE]


Ok, now we are making progress.  This is the contents of your /etc/fstab file.  Currently it has no entry for your XP drive.  So you will need to add a line to the bottom of it, so that the system knows to mount it at startup.

I'm going to post a link to some instructions on how to do it.  Have a read of them, try the instructions and if you have questions along the way, then ask in here again.

You have two options here actually..

Method 1. You can go here and run this script, using the instructions given, and it should automatically edit your fstab file and set you up..   [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions)

or

Method 2. Manually edit yourself using these instructions....
[http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

Now with Method 2. you are probably going to want to know what the linux system is calling your XP partition. Use this command below to get a list of all your partitions..

```
sudo fdisk -l
```

Look for the line in the output that shows an NTFS filesystem, this should be your XP drive.  Note the name /dev/hd??  (?? will vary according to your system).  This is the name you will use in Method 2. to manually edit your fstab file.  The Method 2. instructions are written in a general sense, so you have to subsitute the values that are relevant to your system.

---

### Post by wbsquared on 2006-03-25
[QUOTE=Mustard]Ok, now we are making progress.  This is the contents of your /etc/fstab file.  Currently it has no entry for your XP drive.  So you will need to add a line to the bottom of it, so that the system knows to mount it at startup.

I'm going to post a link to some instructions on how to do it.  Have a read of them, try the instructions and if you have questions along the way, then ask in here again.

You have two options here actually..

Method 1. You can go here and run this script, using the instructions given, and it should automatically edit your fstab file and set you up..   [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions)

or

Method 2. Manually edit yourself using these instructions....
[http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

Now with step 2. you are probably going to want to know what the linux system is calling your XP partition. Use this command below to get a list of all your partitions..

```
sudo fdisk -l
```

Look for the line in the output that shows an NTFS filesystem, this should be your XP drive.  Note the name /dev/hd??  (?? will vary according to your system).  This is the name you will use in Method 2. to manually edit your fstab file.  The Method 2. instructions are written in a general sense, so you have to subsitute the values that are relevant to your system.[/QUOTE]


Thanks a lot for your help, i got the drives mounted and they are accessible.

---

### Post by Mustard on 2006-03-25
[QUOTE=wbsquared]Thanks a lot for your help, i got the drives mounted and they are accessible.[/QUOTE]

A most pleasing result. :)  Well done.

---

### Post by Scunizi on 2006-03-25
One thing to remember that I didn't see mentioned here.... if your entire second HD is NTFS you won't be able to write to it in Linux.  From everything I've read and seen on this forum it's very dangerous to try.  You might mess it up.  I have a similar situation, 2 SATA drives.  The primary is NTFS (80gig) and has XP, the secondary was NTFS (120g).  I installed Breezy and then Dapper on the secondary, shrunk the NTFS partition there, created a small 4gig Vfat partition and had the installer auto partition the rest for the install.  The small Vfat partition I use to copy things from one system to the other if needed.

---

### Post by wbsquared on 2006-03-26
hda1 and hdb1 are showing.  I formatted hda1 with 15 GB for XP, 15 for Linux and its swap, and 10 in fat32 thinking that i would be able to read and write to this partition from both OS's.

Im not sure how to find or access the fat32 10GB partitioned drive but my guess is  that when i go: places>computer, its lists my hard drives (hda1 and hdb1) as well as cd-rom and filesystem.  One more drive is listed as hda5 and im not sure how to access that.  I tried mounting it by right clicking and choosing mount but i get the following error:

       mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Im not sure what to do.

here is a screenshot if this helps anyone visually. 
[[IMG]http://img73.imageshack.us/img73/7091/screenshot5oa.png[/IMG]](http://imageshack.us)

---

### Post by wbsquared on 2006-03-26
I got a list of my partitions

===========
Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1785    14337981    7  HPFS/NTFS
/dev/hda2            3570        4866    10418152+   5  Extended
/dev/hda3   *        1786        3569    14329980   83  Linux
/dev/hda5            3651        4866     9767520    b  W95 FAT32
/dev/hda6            3570        3649      642537   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14946   120053713+   7  HPFS/NTFS
============

So i see that hda5 is the fat32 but how am i supposed to mount it so that i can read and write to the disk???

---

### Post by Mustard on 2006-03-26
I'm surprised that the script didn't recognise the fat32 partition when you ran it.  I guess for that partition you are going to have to edit the fstab file manually and add a line for that partition.  The second link in my instructions above shows you how to do this, if you scroll up the page a bit.  Can you show me the output of this command again so I can get a picture of where we are at atm?

```
cat /etc/fstab
```

---

### Post by wbsquared on 2006-03-26
[QUOTE=Mustard]I'm surprised that the script didn't recognise the fat32 partition when you ran it.  I guess for that partition you are going to have to edit the fstab file manually and add a line for that partition.  The second link in my instructions above shows you how to do this, if you scroll up the page a bit.  Can you show me the output of this command again so I can get a picture of where we are at atm?

```
cat /etc/fstab
```[/QUOTE]
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
#Added by diskmounter utility
/dev/hda1 /media/hda1 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/hdb1 /media/hdb1 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/hda5 /media/hda5 vfat rw,user,fmask=0111,dmask=0000 0 0

```

I used your second link and tried to mount through console manually using the code
```
sudo mkdir /media/windows
 sudo mount /dev/hda5 /media/windows/ -t vfat -o iocharset=utf8,umask=000

```

I still get the error: 

mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by wbsquared on 2006-03-27
Anyone have any idea how i can mount this fat32 partition so i can start reading and writing from linux and XP?

---

### Post by Mustard on 2006-03-27
Try editing the last line of your fstab file (the one that currently refers to your /dev/hda5 to this one below....
```

/dev/hda5    /media/hda5 vfat  iocharset=utf8,umask=000  0    0
```

To open the /etc/fstab file for editing do this..

```
sudo gedit /etc/fstab
```

Edit the last line as above,  then try this..

```
sudo umount /media/hda5

#or if its says its busy

sudo umount /media/hda5 -l


```

Then do this command...

```
sudo mount -a
```

I'm hopeful that this is going to work for you.  :)

NOTE:- Last resort after doing the above.  Reboot the computer (technically not necessary, but sometimes easier than fiddling around with commands).

---

### Post by Minn3h on 2006-03-27
Incidentally, I have found a much easier way of dealing with trading things between operating systems.  Make that partition ext2 or 3 instead of vfat, and install this in Windows to read/write your ext2/3 partition: [http://www.fs-driver.org/](http://www.fs-driver.org/) Very easy to use!

---

### Post by Zerocool10482 on 2006-03-28
Hi I was just wondering how I get my new Sata drive to be listed on Places>Computer. 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
# UNCONFIGURED FSTAB FOR BASE SYSTEM
robert@station-17:~$

Thanks for any of your help.

---

### Post by wbsquared on 2006-03-28
[/QUOTE][QUOTE=Mustard]Try editing the last line of your fstab file (the one that currently refers to your /dev/hda5 to this one below....
```

/dev/hda5    /media/hda5 vfat  iocharset=utf8,umask=000  0    0
```

To open the /etc/fstab file for editing do this..

```
sudo gedit /etc/fstab
```

Edit the last line as above,  then try this..

```
sudo umount /media/hda5

#or if its says its busy

sudo umount /media/hda5 -l


```

Then do this command...

```
sudo mount -a
```

I'm hopeful that this is going to work for you.  :)

NOTE:- Last resort after doing the above.  Reboot the computer (technically not necessary, but sometimes easier than fiddling around with commands).[/QUOTE]

I tried and still receieved the same error as before.  Any other suggestions?  Or should i try another option that was suggested, such as the following:

[QUOTE=Minn3h]
Incidentally, I have found a much easier way of dealing with trading things between operating systems. Make that partition ext2 or 3 instead of vfat, and install this in Windows to read/write your ext2/3 partition: [http://www.fs-driver.org/](http://www.fs-driver.org/) Very easy to use![/QUOTE]

---

### Post by Mustard on 2006-03-28
[QUOTE=wbsquared]I tried and still receieved the same error as before.  Any other suggestions?  Or should i try another option that was suggested, such as the following:[/QUOTE]

What error message are you receiving?  What command are you entering?  What is the the current content of your /etc/fstab file?

I'm quite mystified why it wouldn't work.  I'm assuming there is a typo of some kind in the fstab file atm, so I need to see it again.

Can you also show me the output of this command...

```
ls /media/
```

---

### Post by Zerocool10482 on 2006-03-29
Can you help me with my problem or should I just install ubuntu on my 250g extra drive??

---

### Post by wbsquared on 2006-03-29
[QUOTE=Mustard]What error message are you receiving?  What command are you entering?  What is the the current content of your /etc/fstab file?

I'm quite mystified why it wouldn't work.  I'm assuming there is a typo of some kind in the fstab file atm, so I need to see it again.

Can you also show me the output of this command...

```
ls /media/
```[/QUOTE]

```

ls /media
cdrom  cdrom0  cdrom1  floppy  floppy0  hda1  hda5  hdb1  usb  usb0  windows
```

copy of /etc/fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
#Added by diskmounter utility
/dev/hda1 /media/hda1 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/hdb1 /media/hdb1 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by user
/dev/hda5 /media/hda5 vfat  iocharset=utf8,umask=000  0    0

```

Doing what you said and copying your code to my terminal i recieved the following output after editing the fstab and saving it:

```
 sudo umount /media/hda5
umount: /media/hda5: not mounted

```

i don't know if thats correct but i continued onto the next line:
```

sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

any more ideas, and thanks with your continuing help.

---

### Post by Mustard on 2006-03-29
[QUOTE=Zerocool10482]Can you help me with my problem or should I just install ubuntu on my 250g extra drive??[/QUOTE]

I would highly recommend that you start a new thread, Zerocool.  It's not something that you might know of, but it's not good etiquette in forums to post a different problem in a thread dealing with someone elses problem.  It makes the thread confusing to read and your problem is only seen by people who actually following this particular thread, so your limiting the visibility of your problem in the forum.  A new thread that is exclusively dealing with your issue is the best answer.

---

### Post by Mustard on 2006-03-30
[QUOTE=wbsquared]```

ls /media
cdrom  cdrom0  cdrom1  floppy  floppy0  hda1  hda5  hdb1  usb  usb0  windows
```

copy of /etc/fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
#Added by diskmounter utility
/dev/hda1 /media/hda1 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/hdb1 /media/hdb1 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by user
/dev/hda5 /media/hda5 vfat  iocharset=utf8,umask=000  0    0

```

Doing what you said and copying your code to my terminal i recieved the following output after editing the fstab and saving it:

```
 sudo umount /media/hda5
umount: /media/hda5: not mounted

```

i don't know if thats correct but i continued onto the next line:
```

sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

any more ideas, and thanks with your continuing help.[/QUOTE]


Well I've been staring at this for ages and not seeing what the problem is. :)

The error message being reported give several options for what the problem might be.  I think the we can discount that there is a typo in the line, so bad option is probably not the problem, the line looks perfect for a vfat partition.  So we have the options left of 'wrong filesystem', I'm fairly certain you say this is a vfat partition, so that can be eliminated.  'Missing codepage'?  I have no idea what a codepage is...hehehe..  'Bad superblock'?  Well we could run a file system check on the vfat partition to see if it has errors on it that are causing it to not mount properly.  I would also recommend that you do as the error message says, and try the dmesg | tail command in terminal and look for some error that might describe the problem that the system is having with /dev/hda5.  Additionally you should probably run a fsck (filesystem check) on the **unmounted** device in question, /dev/hda5. fsck needs to be run on an **umounted filesystem** not a mounted one.  You can find out what filesystems are currently mounted by just typing *mount* on its own in the command line.

To use fsck, in the command line try this..

```
sudo fsck /dev/hda5

#the manual for fsck can be accessed by
#typing man fsck in terminal
#press 'q' to exit the manual

```

---

### Post by wbsquared on 2006-03-30
Well the problem is solved. My friend told me to try:

System>Administration>Disks>Partitions

So i tried it, hit enable for the hda5 vfat drive. It didn't work so i just hit format from the same window, so it was reformatted in vfat format.  I then hit enable and the drive was mounted and accessible.

Thanks everyone and especially Mustard for your help.

---

### Post by Mustard on 2006-03-30
[QUOTE=wbsquared]Well the problem is solved. My friend told me to try:

System>Administration>Disks>Partitions

So i tried it, hit enable for the hda5 vfat drive. It didn't work so i just hit format from the same window, so it was reformatted in vfat format.  I then hit enable and the drive was mounted and accessible.

Thanks everyone and especially Mustard for your help.[/QUOTE]

Aha, so the drive was misreporting itself as vfat. Well that was bound to make life confusing. I am very pleased you solved the problem. :)

---

