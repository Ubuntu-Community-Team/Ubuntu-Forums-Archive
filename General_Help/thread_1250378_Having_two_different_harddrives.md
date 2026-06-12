---
title: "Having two different harddrives"
date: 2009-08-26
forum: General Help
---

### Post by WesParmalee on 2009-08-26
Hey, I have installed Ubuntu 8.04 LTS, I'm having a bit of a problem, I have 2 different harddrives, and I don't want them to combine into a large partition. I want the other harddrive to just be a complete seperate drive, apart from the other drive containing Linux, I know I will have to reinstall Ubuntu, it's no problem, but what do I do in the partitioner that will leave my other harddrive a spereate harddrive but still be able to store files I download? Also it would be a huge plus if it could use the same file system as the main drive (Ext3)

Thanks in advance.

:popcorn:

---

### Post by michy99 on 2009-08-26
Unless you have installed some special software, the two drives are separate. I assume you are talking about two physical drives, and not two partitions on the same physical drive. Enter this command in a terminal and post the output here:```
sudo fdisk -l
```

---

### Post by egalvan on 2009-08-26
> **WesParmalee said:**
> I installed Ubuntu 8.04 LTS,,
 I have 2 different harddrives, and I don't want them to combine into a large partition.
 I want the other harddrive to just be a complete seperate drive, apart from the other drive containing Linux, I know I will have to reinstall Ubuntu, it's no problem, but what do I do in the partitioner that will leave my other harddrive a spereate harddrive but still be able to store files I download?

I don't really understand the problem...
but here goes a stab...
 if you don't use LVM ( a means to combine multiples drives)
then all drives are "separate".
Understand, though, that it needs to be mounted onto the root in order to be accessible.

> 
 Also it would be a huge plus if it could use the same file system as the main drive (Ext3)

The drive can formatted to any file system that your software will work with...

MicroSoft
Unix
BSD
Sparc
etc, etc,

As long as you have the software to format, and the the drivers to read/write, it will work...

And Linux comes with a very wide range of file system support.

---

### Post by WesParmalee on 2009-08-26
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         122      979933+  82  Linux swap / Solaris
/dev/sda2   *         123       38913   311588707+  83  Linux

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x115599b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625129281    5  Extended
/dev/sdb5               1       77825   625129249+  83  Linux

Where it says "Extended"

That is a complete physical drive, and I would like to keep it separate from the main drive where Linux is installed, but also I want to use it to keep my downloads in, I hope you can understand what I'm saying heh :)

---

### Post by michy99 on 2009-08-26
This is what you have:

/dev/sda harddrive with two partitions: /dev/sda1 is the linux swap partition and /dev/sda2 is your linux system partition.

/dev/sdb is another hard drive. It has an extended partition (/dev/sdb1) which contains a logical partition (/dev/sdb5) This is a linux partiton so it is either ext3, ext2 or ext4. Can't tell from this listing.

It looks like you have exactly what you want. There really isn't a reason for the Extended/logical setup on sdb, but it isn't hurting anything. You have to mount sdb5 to use it.

---

### Post by egalvan on 2009-08-26
> **WesParmalee said:**
> 

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625129281    5  Extended
/dev/sdb5               1       77825   625129249+  83  Linux

Where it says "Extended"

That is a complete physical drive, and I would like to **keep it separate from the main drive where Linux is installed,** but also I want to use it to keep my downloads in, I hope you can understand what I'm saying heh :)

OK, michy99 gave a good write-up of your hard drive situation.

The extended partition on the second drive is similiar to how I set up my "data" drives, so it's cool with me :)

I guess my problem is that I don't have a clue by what you mean here:

[COLOR="Red"]keep it separate from the main drive where Linux is installed,[/COLOR]

Sorry, but I just don't get it :redface:

There is no way to physically combine drives,
and you need specialized hardware or software to combine them logically...
This is called LVM, or  [COLOR="Red"]L[/COLOR]ogical [COLOR="Red"]V[/COLOR]olume [COLOR="Red"]M[/COLOR]anagement.
(don't confuse with logical [COLOR="Red"]partition[/COLOR], it's totally different)

Sorry.

---

### Post by WesParmalee on 2009-08-26
Ok, I'll try my best to make this clear, I have 2 physical disks, I want Linux to be installed on one hard drive, and I want the second harddrive to be an extra disk that I can access from Places > Computers > 2nd disk

Does this help? 

Thanks a lot for helping

---

### Post by WesParmalee on 2009-08-26
[IMG]http://i31.tinypic.com/k2lgjn.png[/IMG]

Here is a picture, See how it says 1181.1GB? Well that is both my hard drives combined, I don't want this, I would like them to be separate

---

### Post by zolero on 2009-08-26
Hi, **Wes**.

Your wish is very simple to implement. I have it working on my box with a 250 GB and a 500 GB Samsung HDDs exactly how you want it to do. Look at my **fstab** file below (this is responsible for mounting HDDs, DVD drives, floppies, etc. at boot time, and is located in **/etc** folder on the root partition):

```
#==========================================================================================================================================
#
#                       CUSTOMIZED FSTAB - STATIC FILESYSTEM INFORMATIONS - AUTOMATICALLY MOUNTED AT SYSTEM STARTUP
#           ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#
# <file system>    <mount point>    <type>        <options>                        <dump>  <pass>
#
#==========================================================================================================================================
#                      PROC - GENERAL PURPOSE SYS PROCESSES
#==========================================================================================================================================
proc        /proc        proc        defaults                           0       0

#==========================================================================================================================================
#
#                     MOUNTING SWAP & SYSTEM ROOT PARTITIONS
#
#==========================================================================================================================================
/dev/sda1        /        ext2        relatime,errors=remount-ro                   0       1
/dev/sda2        none        swap        sw                           0       0

#==========================================================================================================================================
#
#                     MOUNTING REMAINING STORAGE PARTITIONS ON FIRST HDD
#
#==========================================================================================================================================
/dev/sda3        /media/KEEPER    vfat        uid=1000,gid=1000,dmask=1022,fmask=0133,utf8           0       0
/dev/sda4        /media/STUFFIT    vfat        uid=1000,gid=1000,dmask=1022,fmask=0133,utf8            0     0

#==========================================================================================================================================
#
#                         MOUNTING STORAGE PARTITIONS ON SECOND HDD
#
#==========================================================================================================================================
/dev/sdb1        /media/OFIDOX    ntfs-3g        uid=1000,gid=1000,dmask=1022,fmask=0133,nls=utf8           0     0
/dev/sdb2        /media/SYSBACK    ntfs-3g        uid=1000,gid=1000,dmask=1022,fmask=0133,nls=utf8           0     0
/dev/sdb3        /media/NUCLEUS    ntfs-3g        uid=1000,gid=1000,dmask=1022,fmask=0133,nls=utf8           0     0
/dev/sdb4        /media/ATOMIC    ntfs-3g        uid=1000,gid=1000,dmask=1022,fmask=0133,nls=utf8           0     0

#==========================================================================================================================================
#
#                       MOUNTING OPTICAL DRIVES AND FLOPPY DISK UNITS
#
#==========================================================================================================================================
/dev/scd0        /media/cdrom0    udf,iso9660    user,noauto,exec,utf8                   0       0
/dev/scd1        /media/cdrom1    udf,iso9660    user,noauto,exec,utf8                   0       0
/dev/scd2        /media/cdrom2    udf,iso9660    user,noauto,exec,utf8                   0       0
/dev/fd0        /media/floppy0    auto        rw,user,noauto,exec,utf8                   0       0

#==========================================================================================================================================
#
#                                     MOUNTING DAZUKOFS
#
#==========================================================================================================================================
/home        /home        dazukofs        defaults                           0     0
/opt        /opt        dazukofs        defaults                           0     0
/root        /root        dazukofs        defaults                           0     0
/usr        /usr        dazukofs        defaults                           0     0

```Of course, this is a customized one...  ;)  How to get the same result?  By following few steps...

**1.) **Prepare the mounting places for your partitions (except for filesystem root partition and swap space, that will be done by installer).

```
**sudo mkdir /media/PART_ONE**
**sudo mkdir /media/PART_TWO**
**...**
**sudo mkdir /media/PART_SEVEN**
```... and so on.

Make dirs for how many partitions you intend to create on your drives. No matter which kind of file system they would be, or on which drive they'll be, but equal with their number.

**2.)** Open up ***gparted***'s graphical interface (for more confortable visual editing; if do not have it, just go and install it in usual way) and create your partitions, with desired filesystem(s). You can also format them with this utility (well, if you have installed the supporting stuffs, especially for NTFS ones). Now your drives/partitions are prepared for mounting/usage. Let's mount them at system startup...

**3.)** In this step you need to edit your **fstab** file and tell to the system **what, where, and how** to mount them for you. Use my file as an example. You have to be **root** for doing this. Note that you can badly screwing up your system with this, ending into need of a fresh install. Therefore is highly recommended to have a replacement backup (for just in case).

```
**sudo cp /etc/fstab /etc/fstab_ORIGINAL**
```  --> get the backup;

```
**sudo gedit /etc/fstab**
```  --> now go ahead and do what you need. Save the file after finished and reboot your machine.

When it restarts you'll have your drives/partitions clearly separated, but mounted and ready to work independently each from other. Take a look at [this screenshot]("http://img188.imageshack.us/img188/1671/zlrpartitions.png") to see them mounted separately on my box.

That's it. Hope that this helped.

---

### Post by whitethorn on 2009-08-26
Just for a little clarification, could you post the output to

```
df -h
```

It'll show the different partitions and their respective mountpoints.

---

### Post by michy99 on 2009-08-26
The disk analyzer shows the space on your entire filesystem, which includes both disks. The second disk has to be mounted somewhere in the filesystem for Ubuntu to use it. It is still 'separate' but it is all one filesystem. This is different from the way Windows works with C: and D: and so on.

---

