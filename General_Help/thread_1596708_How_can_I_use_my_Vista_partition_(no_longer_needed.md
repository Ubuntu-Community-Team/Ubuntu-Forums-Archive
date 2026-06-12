---
title: "How can I use my Vista partition (no longer needed)?"
date: 2010-10-14
forum: General Help
---

### Post by hangle on 2010-10-14
Fourteen months ago my Dell computer came with Vista OS. I immediately installed Ubuntu into 2/3 of my disk space and I never used Vista.  I suspect that I kept the MS system as a security blanket that, as of now, I no longer need.

My partitions are:
-----------------------------------------------------------------------------------------------
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1918    15360000    7  HPFS/NTFS
/dev/sda3   *        1918       21600   158095361    7  HPFS/NTFS
/dev/sda4           21601       60801   314882032+   5  Extended
/dev/sda5           60477       60779     2433816   83  Linux
/dev/sda6           60780       60801      176683+  82  Linux swap / Solaris
/dev/sda7           21601       58896   299580057   83  Linux
/dev/sda8           58897       60476    12691318+  82  Linux swap / Solaris
---------------------------------------------------------------------------------------------------------

At first I thought of converting the Vista partition to free space and then claiming this space as a new Ubuntu partition.  I looked into GParted but it seemed like overkill and a way, with my limited knowledge, to lose data. 

I discovered that the Vista partition is mounted by Ubuntu at /media/OS.  I am not sure who mounts it?  The following is the contents of /etc/fstab.
---------------------------------------------------------------------------------------------------
# / was on /dev/sda7 during installation
UUID=1cba46d8-1a35-4077-8e8a-063e4e331885 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=3bfa0a93-b0e5-4d5c-9371-43b6565a87b3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
------------------------------------------------------------------------------------------------------

My question is can I unmount the Vista partition  from /media/OS and mount it elsewhere?

---

### Post by dabl on 2010-10-14
As far as what you _could_ do, you could delete the first 3 partitions and make a single new partition in that space, and use it for data storage or whatever you want.

But as far as what you _should_ do, I have more questions than answers:

1. Why 2 swap partitions?
2. What is the _other_ Linux partition used for?
3. How good are you at setting up /etc/fstab from a console login?
4. How good are you at working with Grub 2 from a console login?

The last 2 questions are due to the likely failures of Grub and device mounting, once the first 3 partitions are replaced by a single partition.  You would have to use fstab and blkid to capture the new partition ID numbers, and edit /etc/fstab and (depending on the answer to #2) perhaps the Grub files, to get it back together.

---

### Post by hangle on 2010-10-14
> **dabl said:**
> As far as what you _could_ do, you could delete the first 3 partitions and make a single new partition in that space, and use it for data storage or whatever you want.

But as far as what you _should_ do, I have more questions than answers:

1. Why 2 swap partitions?
2. What is the _other_ Linux partition used for?
3. How good are you at setting up /etc/fstab from a console login?
4. How good are you at working with Grub 2 from a console login?

The last 2 questions are due to the likely failures of Grub and device mounting, once the first 3 partitions are replaced by a single partition.  You would have to use fstab and blkid to capture the new partition ID numbers, and edit /etc/fstab and (depending on the answer to #2) perhaps the Grub files, to get it back together.


I have always wondered about the (1) and (2) questions that you posed; it did seem strange to me.  I probably caused it when i messed up with the  first installation of ubuntu.  i misunderstood the partition procedure and allocated insufficient disk space for ubuntu.  i re installed ubuntu over the first installation and got sufficient space; but the first installation did not go away.  

to answer your third and fourth question-- I am not up to the task.  i know if i start changing partitions i am going to mess the table up.

---

### Post by dabl on 2010-10-14
Unless you are hurting for disk space for your data, it sounds like you might be better off leaving it alone for now.

For future consideration, I'll share some tips:

1. Download [[COLOR="SeaGreen"]**Parted Magic**[/COLOR]](http://partedmagic.com/download.html), and make either a bootable Live CD or a USB stick, as you prefer.  Then, use that to take care of disk partitioning and filesystem formatting in advance of installing Linux.  That way, you can use an Alternate Install CD, and _just_ install the OS, skipping the partitioning stage where all these problems like extra swap partitions tend to get created.

2. Once you have a disk or disks with formatted partitions, and perhaps even data on them, and you've installed Ubuntu, and you need to fix /etc/fstab so they are mounted automatically, the easiest way I know to do it right is to open 2 terminal windows.  In one you run ```
sudo fdisk -lu
``` and in the other one you run ```
sudo blkid
```

Then open gedit (or kate for KDE) in root mode, and use it for editing /etc/fstab.

By looking at the fdisk output, it's pretty easy to tell which partitions are on which hard drive, and what the filesystem type for each partition is.  By comparing that to the blkid output, you can tell which UUID belongs to each partition.  So, you edit /etc/fstab to make a boot line for each partition that you want mounted, using the UUID number, and the filesystem type as you see it in the terminal windows.

If you only have the one OS on the computer, then the Grub settings are not a problem.  If you are dual booting some other OS, then that can add another complication to your setup.

Hope this helps.

---

### Post by srs5694 on 2010-10-14
A few more comments:


[list]
[*]Your NTFS partition is being mounted by the GNOME automounter. This action occurs when you log into the computer and it's handled by probing for available partitions dynamically, rather than by /etc/fstab, which makes more permanent and static configurations. If you want the automounter to ignore the NTFS partition, you can create an /etc/fstab entry -- even one that explicitly says to *not* mount the partition.
[*]If you're completely abandoning Windows, *do not* attempt to use the Windows partition as-is for data storage. The reason is that it currently uses NTFS, and Linux has no adequate NTFS maintenance tools. Thus, if your system crashes or if you suffer a power failure, the disk will be in an inconsistent state and Linux may well refuse to mount it. It will then be more difficult to recover, since you'll need to locate Windows recovery tools on CD/DVD to do the job. If you find yourself in need of the disk space, you can convert it for Linux use by creating a Linux filesystem (ext3fs, ext4fs, ReiserFS, XFS, JFS, or even Btrfs if you're feeling adventurous) on it.
[*]When you're up for it, you could look into using [Logical Volume Manager,](http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29) which is a way of aggregating storage space on multiple partitions into a space that can then be subdived in other ways. In your case, you could convert the three Windows partitions and two unused Linux partitions into LVM partitions. You'll then be able to create logical volumes in this space, re-allocating it in whatever way is convenient -- one big filesystem bigger than any one partition, several smaller filesystems, or whatever. You could migrate your current installation into an LVM setup in a fairly risk-free way, without repartitioning. There is a learning curve to LVM, but aside from converting the partitions into LVM partitions, the risk to your current installation is low, so this could be a reasonable medium- to long-term project.
[/list]

---

### Post by hangle on 2010-10-15
I suspected that i oversimplified the situation.  thank you for the warning regarding using the NTFS files.  

Are you suggesting that i could convert the MS file types to linux ones? 

I am looking into the Logical Volume Manager.  I am finding this forum to be a great learning experience. 

Thanks.

---

### Post by srs5694 on 2010-10-15
You can change a partition from NTFS to a Linux-native filesystem by using mkfs or a similar utility. For instance, if you want to convert /dev/sda3, you'd type:

```

sudo mkfs -t ext3 /dev/sda3

```

You can change ext3 to another partition type code, like ext4 or xfs. Thereafter, you can mount it normally. Be sure to get the partition filename correct; if you mistype "/dev/sda3" as "/dev/sda5", for instance, you might damage your Linux installation.

One caveat: This procedure changes the *filesystem* on the partition, but not the *type code* associated with the partition to change the type code, you could use fdisk: Type "sudo fdisk /dev/sda", then use the "t" option to change the type code. Type "p" to verify that your change is correct, and type "w" to save the change. Linux ignores the type code for most purposes, so changing it isn't strictly necessary in the short term. Having the wrong type code can be confusing and could lead to errors down the line, particularly if some automated utility gets confused and decides that, say, /dev/sda3 is a badly corrupted NTFS volume and tries to repair it as such.

Tools based on libparted, such as GParted, can make both changes at once.

---

