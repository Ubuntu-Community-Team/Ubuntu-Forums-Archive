---
title: "Problems accessing 2nd hdd"
date: 2012-09-17
forum: General Help
---

### Post by sfourie on 2012-09-17
I cannot access my data on my second hdd. I made a copy of the os (ubuntu 12.04) onto the second hdd. I assumed it will take the existing space used on main hdd and copy onto the second hdd which had more than enough space.

Once done, the pc now boots using main hdd, but os runs off 2nd hdd. All my data (music, etc) are lost. i cannot access it.
Is it deleted, is that partition not accessable?


Can you please help.

---

### Post by Bashing-om on 2012-09-17
sfourie;

To see your 2nd hard drive ....do this, booted into the first hard drive (bios is set to boot from 1st hard drive ?)
```
sudo mkdir /mnt/my-stuff
sudo mount /dev/sdb1 /mnt/my-stuff
sudo chown <your-user-name>:<your-user-name> /mnt/my-stuff/<desired directories>
``` This is assuming the 2nd drive is recognized as "sdb" and "sdb1" holds "/".
adjust as needed. 
to un mount the drive 
```
sudo umount /mnt/my-stuff
```If this is acceptable, we can make the mount auto-mount by editing /etc/fstab[INDENT]regards <==BDQ

[/INDENT]

---

### Post by ajgreeny on 2012-09-17
I do not understand what you are saying, I'm afraid, so let's start at the beginning and see what you did.

How did you copy your OS and put it on the second HDD?
What do you mean by "the pc now boots using main hdd, but os runs off 2nd hdd."  Is grub still on the main disk but the ubuntu OS on the second disk?
What filesystem was the second HDD when you copied the OS onto it?  I assume it must have been ext4 (ext3 maybe) or ubuntu would not boot.

Can you open a terminal and show us the output of ```
sudo fdisk -lu
``` to see what partitions are present and the formatted filesystems of them.

---

### Post by sfourie on 2012-09-18
I wanted to create a backup of Ubuntu 12.04 with all updates etc. to date. I tried to do research on cutting/burning a live cd, but I am not that clued up to know if it will do what I aimed doing.

In bios the pc is set to boot from the Hitachi hdd which is sdb according to Ubuntu.

So I put a command into terminal to copy os (exact command I can't remember). So what has happened it copied the whole sdb disk onto sda. Ubuntu ran off sdb. Then when I started the pc after it copied, Ubuntu ran off sdb,

The second hdd was ext4 yes.


Here are the specs of the disks:

  	 	 	 	 	 	   **Uuid:**
 /dev/sda5: UUID="df695ccc-3016-4d9b-b981-11f924fadd07" TYPE="ext4" 
 /dev/sdb1: UUID="df695ccc-3016-4d9b-b981-11f924fadd07" TYPE="ext4" 
 /dev/sdb5: UUID="5282e75c-c686-4fae-8242-6bfc21ae882a" TYPE="swap" 
 

 **fdisk:**
 stefan@hettie-desktop:~$ sudo fdisk -l  
 

 Disk /dev/sda: 160.0 GB, 160041885696 bytes  
 255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Sector size (logical/physical): 512 bytes / 512 bytes  
 I/O size (minimum/optimal): 512 bytes / 512 bytes  
 Disk identifier: 0x71251de1  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1   *          63       16064        8001    7  HPFS/NTFS/exFAT  
 /dev/sda2           16065   312576704   156280320    5  Extended  
 /dev/sda5           16128   312576704   156280288+   7  HPFS/NTFS/exFAT  
 

 Disk /dev/sdb: 160.0 GB, 160041885696 bytes  
 255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Sector size (logical/physical): 512 bytes / 512 bytes  
 I/O size (minimum/optimal): 512 bytes / 512 bytes  
 Disk identifier: 0x00054d84  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sdb1   *        2048   310519807   155258880   83  Linux  
 /dev/sdb2       310521854   312580095     1029121    5  Extended  
 /dev/sdb5       310521856   312580095     1029120   82  Linux swap / Solaris
 

 **cat /etc/fstab**
 stefan@hettie-desktop:~$ cat /etc/fstab 
 # /etc/fstab: static file system information.  
 #  
 # Use 'blkid' to print the universally unique identifier for a  
 # device; this may be used with UUID= as a more robust way to name devices  
 # that works even if disks are added and removed. See fstab(5).  
 #  
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>  
 proc            /proc           proc    nodev,noexec,nosuid 0       0  
 # / was on /dev/sda1 during installation  
 UUID=df695ccc-3016-4d9b-b981-11f924fadd07 /               ext4    errors=remount-ro 0       1  
 # swap was on /dev/sda5 during installation  
 UUID=5282e75c-c686-4fae-8242-6bfc21ae882a none            swap    sw              0       0  
 

 **stefan@hettie-desktop:~$ cat /etc/mtab ** 
 /dev/sda5 / ext4 rw,errors=remount-ro 0 0  
 proc /proc proc rw,noexec,nosuid,nodev 0 0  
 sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0  
 none /sys/fs/fuse/connections fusectl rw 0 0  
 none /sys/kernel/debug debugfs rw 0 0  
 none /sys/kernel/security securityfs rw 0 0  
 udev /dev devtmpfs rw,mode=0755 0 0  
 devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0  
 tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0  
 none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0  
 none /run/shm tmpfs rw,nosuid,nodev 0 0 
 binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0  
 gvfs-fuse-daemon /home/stefan/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=stefan 0 0

---

### Post by sfourie on 2012-09-18
I have taken screen shots of the disk utility, maybe it can assist more in assessing the problem.

Thank you for your help thus far.

---

### Post by sfourie on 2012-09-18
I wanted to create a backup of Ubuntu 12.04 with all updates etc. to  date. I tried to do research on cutting/burning a live cd, but I am not  that clued up to know if it will do what I aimed doing.

In bios the pc is set to boot from the Hitachi hdd which is sdb according to Ubuntu.

So I put a command into terminal to copy os (exact command I can't  remember). So what has happened it copied the whole sdb disk onto sda.  Ubuntu ran off sdb. Then when I started the pc after it copied, Ubuntu  ran off sdb,

The second hdd was ext4 yes.


Here are the specs of the disks:

  	 	 	 	 	 	   **Uuid:**
 /dev/sda5: UUID="df695ccc-3016-4d9b-b981-11f924fadd07" TYPE="ext4" 
 /dev/sdb1: UUID="df695ccc-3016-4d9b-b981-11f924fadd07" TYPE="ext4" 
 /dev/sdb5: UUID="5282e75c-c686-4fae-8242-6bfc21ae882a" TYPE="swap" 
 

 **fdisk:**
 stefan@hettie-desktop:~$ sudo fdisk -l  
 

 Disk /dev/sda: 160.0 GB, 160041885696 bytes  
 255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Sector size (logical/physical): 512 bytes / 512 bytes  
 I/O size (minimum/optimal): 512 bytes / 512 bytes  
 Disk identifier: 0x71251de1  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1   *          63       16064        8001    7  HPFS/NTFS/exFAT  
 /dev/sda2           16065   312576704   156280320    5  Extended  
 /dev/sda5           16128   312576704   156280288+   7  HPFS/NTFS/exFAT  
 

 Disk /dev/sdb: 160.0 GB, 160041885696 bytes  
 255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors  
 Units = sectors of 1 * 512 = 512 bytes  
 Sector size (logical/physical): 512 bytes / 512 bytes  
 I/O size (minimum/optimal): 512 bytes / 512 bytes  
 Disk identifier: 0x00054d84  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sdb1   *        2048   310519807   155258880   83  Linux  
 /dev/sdb2       310521854   312580095     1029121    5  Extended  
 /dev/sdb5       310521856   312580095     1029120   82  Linux swap / Solaris
 

 **cat /etc/fstab**
 stefan@hettie-desktop:~$ cat /etc/fstab 
 # /etc/fstab: static file system information.  
 #  
 # Use 'blkid' to print the universally unique identifier for a  
 # device; this may be used with UUID= as a more robust way to name devices  
 # that works even if disks are added and removed. See fstab(5).  
 #  
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>  
 proc            /proc           proc    nodev,noexec,nosuid 0       0  
 # / was on /dev/sda1 during installation  
 UUID=df695ccc-3016-4d9b-b981-11f924fadd07 /               ext4    errors=remount-ro 0       1  
 # swap was on /dev/sda5 during installation  
 UUID=5282e75c-c686-4fae-8242-6bfc21ae882a none            swap    sw              0       0  
 

 **stefan@hettie-desktop:~$ cat /etc/mtab ** 
 /dev/sda5 / ext4 rw,errors=remount-ro 0 0  
 proc /proc proc rw,noexec,nosuid,nodev 0 0  
 sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0  
 none /sys/fs/fuse/connections fusectl rw 0 0  
 none /sys/kernel/debug debugfs rw 0 0  
 none /sys/kernel/security securityfs rw 0 0  
 udev /dev devtmpfs rw,mode=0755 0 0  
 devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0  
 tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0  
 none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0  
 none /run/shm tmpfs rw,nosuid,nodev 0 0 
 binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0  
 gvfs-fuse-daemon /home/stefan/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=stefan 0 0

---

### Post by Bashing-om on 2012-09-18
sfourie;

  I remain confused ....here is what you have;
Your first disk is windows (fdisk confirms) [sda]
your second disk is linux ( ubuntu 12.04 ?)
now: uuid places sda5 as formated with linux ext4 AND fdisk places the same sda5 as 
/dev/sda5           16128   312576704   156280288+   7  HPFS/NTFS/exFAT  . fstab is attempting to boot with sda1 as root with ext4 formatting. However fdsik portrays all of sda as windows.  At the present time I do not comprehend how this is possible.

Before we proceed, what is your intent ? Dual boot with windows on the first drive (sda) and ubuntu on the second (sdb)?

Wipe windows from sda installing ubuntu then sdb as an image of sda ?

As of now ....what data on which operating system do you want to access ? 
[INDENT][INDENT]regards <==BDQ
[/INDENT][/INDENT]

---

### Post by oldfred on 2012-09-18
You did some sort of image copy so the UUID is identical. You cannot have two UUIDs that are the same. You fstab specifies the UUID but does not know which to use or randomly uses one or the other.

> /dev/sda5: UUID="df695ccc-3016-4d9b-b981-11f924fadd07" TYPE="ext4" 
 /dev/sdb1: UUID="df695ccc-3016-4d9b-b981-11f924fadd07" TYPE="ext4" 

You have to change UUID in sdb1, update fstab with new UUID and reinstall grub so it sees the new UUID.

---

### Post by Bashing-om on 2012-09-18
@ oldfred, Thanks I am relieved you are watching our progress.
I have directed our op to stay in the public view with this.

[INDENT][INDENT]BDQ

[/INDENT][/INDENT]

---

### Post by sfourie on 2012-09-18
I don't have windows installed at all. I have ubuntu installed ond sdb. Then sda (which is an older disk) I took from another pc, deleted windows and obviously kept the data I had on there. I then snstalled it and Ubuntu identified it as an nfts disk. It worked fine, but had no os on it.

---

### Post by Bashing-om on 2012-09-18
ok, so what we have is sda as a "data" disk formated with ntfs, that you wish to access from the "copied" sdb disk.

 You want to repair sdb to boot from as the only operating system ?

[INDENT]regards ==>BDQ
[/INDENT]

---

### Post by sfourie on 2012-09-18
sdb works as the main hdd as it is the only disk with a bootable os. My intent is not a dual boot, just to have a backup of an up to date os with updates.

---

### Post by sfourie on 2012-09-18
The sdb disk is not the copied disk, but was the main disk in the pc. the sda disk is a formatted nfts disk that has the copied ubuntu os on

---

### Post by sfourie on 2012-09-18
sdb is set as the boot cd. I want to access my data on sda

---

### Post by sfourie on 2012-09-18
So will the following changes solve my problem:
Quote:
You did some  sort of image copy so the UUID is identical. You cannot have two UUIDs  that are the same. You fstab specifies the UUID but does not know which  to use or randomly uses one or the other.

 	Quote:
 	 	 		 			 				/dev/sda5: UUID="df695ccc-3016-4d9b-b981-11f924fadd07" TYPE="ext4" 
 /dev/sdb1: UUID="df695ccc-3016-4d9b-b981-11f924fadd07" TYPE="ext4" 			 		 	 	 
You have to change UUID in sdb1, update fstab with new UUID and reinstall grub so it sees the new UUID.
 		                   		  		  		 		 			 				__________________
				[COLOR=Navy]Let us know what works and to mark your thread as[/COLOR] [SOLVED][COLOR=Navy], use [COLOR=Red]Thread Tools[/COLOR] on forum page. 
Howto: [https://wiki.ubuntu.com/UnansweredPo.../SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

Can i then access my data on the nfts partition?
[/COLOR]

---

### Post by Bashing-om on 2012-09-18
My regrets => continued confusion on my part.
1. sda is formated with windows formatting, as ubuntu format is ext4, ubuntu can not run on the drive (hold as data yes)
2. We can rebuild sdb's fstab to boot all partitions properly and install grub properly.


But ...IF you have no valuable data to save on sda ...why not do a fresh install to sda ?
OR physically swap the drives within the drive bays, fix fstab accordingly .. and then clone ubuntu onto the present ntfs formatted drive ?

I require direction as to what you want to do. ==>BDQ

---

### Post by sfourie on 2012-09-18
I have valuable data on sda. Well I hope I have. I used sdb as main drive for os with very little data on it. sda was my data disk with all my music, documents, photos, work docs etc on there. So yes I want to access my old data before the os was copied from sdb onto sda. 
Did you view the screen shots I attached previously in the thread?
So I don't want to format sda if i can access the data. If not then I have to format and do a data recovery.

---

### Post by oldfred on 2012-09-18
I do not know if fixing UUID issue will solve you other issue, but system will not work correctly with duplicate UUIDs.

Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX

Then you have to manually edit fstab with new UUID.
sudo mkdir /mnt/sdb1
sudo mount /dev/sda1 /mnt/sdb1
gksudo gedit /mnt/sdb1/etc/fstab


Technically you have to chroot into the partition to run the sudo update grub, but it may be easier just to edit grub.cfg (which we normally do not edit). You only have to change first grub entry with new UUID, so you can boot. Then you can run the sudo update-grub from inside your install.

grub.cfg is read only and should not normally be edited:
sudo chattr -i /mnt/sdb1/boot/grub/grub.cfg
#and / or to get past read only setting:
gksudo gedit +28 /mnt/sdb1/boot/grub/grub.cfg

---

### Post by sfourie on 2012-09-18
Thank  you kindly for all assistance.
i will try that tomorrow. It is almost the early hours of the morning here and I need rest.
Can I continue with the thread tomorrow? 
Will I be able to get valuable assistance like I did from all today?

---

### Post by Bashing-om on 2012-09-18
Got it straight in my mind, thanks.
Most assuredly on continued support.
old freds suggestions are much more elegant than I had in mind. Please, when you are prepared, follow old fred's advise. Once your ubuntu is functional, we will enable you to access sda's data.

[INDENT][INDENT]regards <== BDQ

[/INDENT][/INDENT]

---

### Post by sfourie on 2012-09-19
Hello BDQ and Oldfred
I have executed commands as suggest, here are the response on terminal:
tefan@hettie-desktop:~$ tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
tune2fs 1.42 (29-Nov-2011)
tune2fs: No such file or directory while trying to open /dev/sdaX
Couldn't find valid filesystem superblock.
stefan@hettie-desktop:~$ sudo tune2fs -U random /dev/sdaX
[sudo] password for stefan: 
tune2fs 1.42 (29-Nov-2011)
tune2fs: No such file or directory while trying to open /dev/sdaX
Couldn't find valid filesystem superblock.
stefan@hettie-desktop:~$ sudo mkdir /mnt/sdb1
stefan@hettie-desktop:~$ sudo mount /dev/sda1 /mnt/sdb1
mount: you must specify the filesystem type
stefan@hettie-desktop:~$ sudo mount /dev/sda1 /mnt/dev/sdb1
mount: mount point /mnt/dev/sdb1 does not exist
stefan@hettie-desktop:~$ 
What do i do now?

---

### Post by oldfred on 2012-09-19
You are supposed to replace the X with the drive. It was meant to be a generic command. I guess I should have been more clear. You also have to copy & paste the number generated by uuidgen into the command.

And I had a typo in the mount command which makes it confusing. The device & mount should be the same. But if already mounted by Nautilus or other ways it will not mount and for some formats mount needs to be told exactly what format to use to mount it. 

So lets confirm that we are working on sdb1.
```

sudo fdisk -lu
```

Make sure you do not have it mounted any place else.
```
mount
```

Verify that sdb1 is not mounted.
Lets use this which was the second option and only run if sdb1 is the partition we want to change:
```

sudo tune2fs -U random /dev/sdb1
```

Then list the new UUID as we will need to copy this into fstab:
```

sudo blkid -c /dev/null -o list
```

---

### Post by sfourie on 2012-09-19
stefan@hettie-desktop:~$ **sudo fdisk -lu**
[sudo] password for stefan: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x71251de1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63       16064        8001    7  HPFS/NTFS/exFAT
/dev/sda2           16065   312576704   156280320    5  Extended
/dev/sda5           16128   312576704   156280288+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00054d84

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   310519807   155258880   83  Linux
/dev/sdb2       310521854   312580095     1029121    5  Extended
/dev/sdb5       310521856   312580095     1029120   82  Linux swap / Solaris
stefan@hettie-desktop:~$

---

### Post by sfourie on 2012-09-19
Mount
stefan@hettie-desktop:~$ mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/stefan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=stefan)
stefan@hettie-desktop:~$

---

### Post by sfourie on 2012-09-19
stefan@hettie-desktop:~$ **sudo tune2fs -U random /dev/sdb1**
tune2fs 1.42 (29-Nov-2011)
stefan@hettie-desktop:~$

---

### Post by sfourie on 2012-09-19
new list:
stefan@hettie-desktop:~$ sudo blkid -c /dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda5  ext4    /dev/sda5/media/ /      df695ccc-3016-4d9b-b981-11f924fadd07
/dev/sdb1  ext4             (not mounted)  5f0f85ba-807a-4169-95e6-15046bac0646
/dev/sdb5  swap             <swap>         5282e75c-c686-4fae-8242-6bfc21ae882a
stefan@hettie-desktop:~$

---

### Post by oldfred on 2012-09-19
Now you need to copy this new UUID into fstab in sdb1 and into grub.cfg in sdb1.

  > 5f0f85ba-807a-4169-95e6-15046bac0646

It looks like you had sdb1 mounted as /, so I am not sure where you are at.

> /dev/sdb1 on / type ext4 (rw,errors=remount-ro)

But I do not know where you are? are you still booted or did the UUID change unmount / so you are not running? Or are you now on liveCD?

---

### Post by sfourie on 2012-09-19
No it looks like it unmounted. sda is mounted (which is the copied os) and sdb (original installation) not mounted. I am not running off a live cd

---

### Post by sfourie on 2012-09-19
Yes, sdb1 is mounted as/ I don't know what it means. As mentioned before sdb is the disk that had the os originally installed on.

How do I copy the new uuid into fstab.
Sorry i am still very new at this.

---

### Post by Bashing-om on 2012-09-19
would it help us to compare mtab to what is now in fstab ?

[INDENT][INDENT]BDQ
[/INDENT][/INDENT]

---

### Post by sfourie on 2012-09-19
I am not sure what mtab is, but if I run:    ls /dev/disk/by-uuid i see the new uuid shows, but I am not usre if it is copied in fstab and grub. that is point 1. Pointo 2 is if not, how do I do it?

---

### Post by oldfred on 2012-09-19
Definitely a good idea Bashing-om. I am lost on how system is currently running and which is old & which is new install. I thought sdb1 was the new copy?

Post these:
cat /etc/fstab
cat /etc/mtab

---

### Post by oldfred on 2012-09-19
If you are in your system, but if it is unmounted, we have to mount it either from your old working install or the liveCD and then the mount point is different:

sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

and we need to confirm which fstab we are editing, the old or the new copy.

Just to make sure we are not editing wrong one, I think we need to boot into liveCD and specifically mount the  partition that we want to edit.

Best to post a new BootInfo from this:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by sfourie on 2012-09-19
stefan@hettie-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=df695ccc-3016-4d9b-b981-11f924fadd07 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5282e75c-c686-4fae-8242-6bfc21ae882a none            swap    sw              0       0
##/dev/sdb
UUID=<5f0f85ba-807a-4169-95e6-15046bac0646>/media/sdb1 ntfs defaults 01
stefan@hettie-desktop:~$

---

### Post by sfourie on 2012-09-19
MTAB:
stefan@hettie-desktop:~$ cat /etc/mtab
/dev/sdb1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/stefan/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=stefan 0 0
gvfs-fuse-daemon /root/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev 0 0
stefan@hettie-desktop:~$

---

### Post by oldfred on 2012-09-19
It looks like you still are mounted even though the underlying system has changed.

Lets see if we can directly edit fstab before rebooting.

sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

copy entry from sdb1 into fstab replacing the one that was sda1.

```
/dev/sda5  ext4    /dev/sda5/media/ /      df695ccc-3016-4d9b-b981-11f924fadd07
/dev/sdb1  ext4             (not mounted)  [COLOR=Red]5f0f85ba-807a-4169-95e6-15046bac0646[/COLOR]
/dev/sdb5  swap             <swap>         5282e75c-c686-4fae-8242-6bfc21ae882a

``````
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation [COLOR=Red]changed to sdb1[/COLOR]
UUID=[COLOR=Red]df695ccc-3016-4d9b-b981-11f924fadd07[/COLOR] /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5282e75c-c686-4fae-8242-6bfc21ae882a none            swap    sw              0       0
##/dev/sdb
[COLOR=Red]#[/COLOR]UUID=[COLOR=Blue]<5f0f85ba-807a-4169-95e6-15046bac0646>[/COLOR]/media/sdb1 ntfs defaults 01


```Also put a # in front of last entry. < > should not be there and sdb1 is ext4 not NTFS

Then run this and see if you get any errrors

mount

---

### Post by sfourie on 2012-09-19
i did as you said. I ran mount
This is the result:
stefan@hettie-desktop:~$ mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/stefan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=stefan)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
stefan@hettie-desktop:~$

---

### Post by oldfred on 2012-09-19
Lets try 

```
sudo mount -a
```

Hopefully no errors, if it just returns to command line that is good.

---

### Post by sfourie on 2012-09-19
Ok, it is mounted, but if I am correct, it is sdb that is now mounted. am I correct? So now we need to set sdb as boot drive. then i need to access the data on sda5. Sorry i know it is time consuming and it frustrates me but I honestly do appreciate your help

---

### Post by oldfred on 2012-09-19
That takes care of fstab for booting.

If you are still booted.
```

sudo update-grub
```And that should update grub.cfg.

---

### Post by sfourie on 2012-09-19
grub:
stefan@hettie-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-30-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-30-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 12.04.1 LTS (12.04) on /dev/sdb1
done
stefan@hettie-desktop:~$ 

Wonderful, so now I will boot automatically from sdb1 again. that is wonderful.
Thank you kindly.
I appreciate it.
Can we now try and access my old data on sda5?

---

### Post by oldfred on 2012-09-19
Do we have grub correctly installed to sdb? and BIOS set to boot from SDB?

Just to be sure. Grub remembers where to reinstall and we want it to reinstall to sdb.

#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

Be sure to choose the drive that is sdb. You then can double check above command to see that it will reinstall to the drive that is sdb.
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by sfourie on 2012-09-19
this is all greek to me:
stefan@hettie-desktop:~$ sudo debconf-show grub-pc
  grub2/kfreebsd_cmdline:
* grub2/linux_cmdline:
  grub-pc/install_devices_failed: false
  grub-pc/chainload_from_menu.lst: true
  grub-pc/postrm_purge_boot_grub: false
  grub2/kfreebsd_cmdline_default: quiet
* grub2/linux_cmdline_default: quiet splash
  grub-pc/hidden_timeout: true
* grub-pc/install_devices: /dev/disk/by-id/ata-Hitachi_HDP725016GLA380_GEM864RS1V95BP
  grub-pc/partition_description:
  grub2/device_map_regenerated:
  grub-pc/kopt_extracted: false
  grub-pc/disk_description:
  grub-pc/install_devices_empty: false
  grub-pc/timeout: 10
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/install_devices_disks_changed:
  grub-pc/mixed_legacy_and_grub2: true
stefan@hettie-desktop:~$

---

### Post by sfourie on 2012-09-19
stefan@hettie-desktop:~$ **sudo grub-probe -t device /boot/grub**
/dev/sda5
stefan@hettie-desktop:~$

---

### Post by oldfred on 2012-09-19
Is this your second hard drive?

```
* grub-pc/install_devices: /dev/disk/by-id/ata-Hitachi_HDP725016GLA380_GEM864RS1V95BP
```BIOS should also show it the same way or something like Hitachi and model number.

Edit - You added this while I was creating this post.
stefan@hettie-desktop:~$ **sudo grub-probe -t device /boot/grub**
/dev/sda5
We want that to be sdb1. So run the second part (sudo dpkg ...) posted above to totally reinstall grub to the drive that is  sdb.

What name/mount point do you want to use for your NTFS data partition sda5? In Windows it will be d: if second partition, but in Linux you can give it just about any name.

And where do you want to mount it?
Mount in /media or /home will show in Nautilus left panel, mounts in / or /mnt will not.
I mount my shared in /mnt/shared, but link folders from my shared into /home. That way the top level shared does not show in nautilus but all the folders I want to see from shared are in /home if that makes sense.

You will need to make the mount point and edit fstab again. You can change the [COLOR=Red]WinD[/COLOR] to anything, just create mount and entry in fstab with exactly the same spelling and capitalization. Also no spaces.

sudo mkdir /media/[COLOR=Red]WinD[/COLOR]
sudo cp /etc/fstab /etc/fstab.backup2
gksu gedit /etc/fstab

Add this line - confirm that I copied UUID correctly and make sure to have spaces beteen the last two 0 0 .

```
UUID=df695ccc-3016-4d9b-b981-11f924fadd07 /media/[COLOR=Red]WinD[/COLOR] ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0

```Again to make sure there are no typos:
sudo mount -a

---

### Post by sfourie on 2012-09-19
Yes the Hitachi is my sdb hdd. It is the hdd that i loaded Ubuntu on.
The sda5 i want to name StefanHD then i know it is my hdd.
I uased to mount it in /media.
I would prefer to mount it there again.
I understand the concept of  what you did with your sharing, and it is a great idea. I will certainly do that once all is sorted and data moved around and backed up.
I will run the commands and make the mount point.
Thank you for all your assistance thus far.

---

### Post by sfourie on 2012-09-19
The changes as you suggested:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=df695ccc-3016-4d9b-b981-11f924fadd07 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5282e75c-c686-4fae-8242-6bfc21ae882a none            swap    sw              0       0
##/dev/sdb
#UUID=<5f0f85ba-807a-4169-95e6-15046bac0646>/media/sdb1 ntfs defaults 01
UUID=df695ccc-3016-4d9b-b981-11f924fadd07 /media/StefanHD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 00

---

### Post by sfourie on 2012-09-19
**Result of sudo mount -a**
stefan@hettie-desktop:~$ sudo mount -a
NTFS signature is missing.
Failed to mount '/dev/sda5': Invalid argument
The device '/dev/sda5' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
stefan@hettie-desktop:~$ 

It does not seem to be good news

---

### Post by sfourie on 2012-09-19
Sorry my mistake:
Herewith the corrected fstab with spaces between the 00:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=df695ccc-3016-4d9b-b981-11f924fadd07 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5282e75c-c686-4fae-8242-6bfc21ae882a none            swap    sw              0       0
##/dev/sdb
#UUID=<5f0f85ba-807a-4169-95e6-15046bac0646>/media/sdb1 ntfs defaults 01
UUID=df695ccc-3016-4d9b-b981-11f924fadd07 /media/StefanHD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0

---

### Post by oldfred on 2012-09-19
That looks good. Did the sudo mount -a just return. Then it should be good.

Did you run the dpkg command to install grub to sdb?
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions - I think arrow keys move up & down & spacebar selects. Just be sure to select the drive that is sdb. see below to list drives if unsure.


If you want to see the drives:

fred@fred-Precise:~$ [COLOR=Red]sudo lshw -C Disk -short[/COLOR]
[sudo] password for fred: 
```
H/W path             Device      Class       Description
========================================================
/0/100/1f.2/0        /dev/sda    disk        160GB MAXTOR STM316081
/0/100/1f.2/1        /dev/cdrom  disk        CD/DVDW SH-S183L
/0/100/1f.2/2        /dev/sdc    disk        160GB MAXTOR STM316081
/0/100/1f.2/3        /dev/sdd    disk        640GB WDC WD6400AACS-0
/0/100/1f.2/0.0.0    /dev/sde    disk        60GB SSD G2 series 64
/0/1/0.0.0           /dev/sdb    disk        4043MB SCSI Disk

```

I have to mow lawn, be back in an hour.

---

### Post by sfourie on 2012-09-19
Thank you kindly.
It seems to be ok.
Good luck with mowing of the lawn.
I am off to bed.
Here are the details after running dpkg.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-30-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-30-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 12.04.1 LTS (12.04) on /dev/sdb1
done
stefan@hettie-desktop:~$ 

So it seems to be fine.

Now i need to access my old data if possible.
If you are available tomorrow can you please assist me with it.
Thank you

---

### Post by sfourie on 2012-09-19
My list of disks:
stefan@hettie-desktop:~$ sudo lshw -C Disk -short
H/W path           Device       Class       Description
=======================================================
/0/100/1f.2/0      /dev/sda     disk        160GB MAXTOR STM316021
/0/100/1f.2/1      /dev/sdb     disk        160GB Hitachi HDP72501
/0/100/1f.2/0.1.0  /dev/cdrom1  disk        DVDRAM GH22LS40
stefan@hettie-desktop:~$

---

### Post by oldfred on 2012-09-19
Partition table showed sda5 as NTFS. But it was ext3 or 4 for Linux before? How did you reformat it?

NTFS partition have to have a NTFS signature in the PBR or partition boot sector. There are at least two types, one to boot XP with ntldr and the other for Vista/7 that says use bootmgr. I am not sure if there is a third where it is just formatted but is not bootable. I think only the boot flag controls bootable. In Windows the partition may be shown as RAW or unformated.

Did you have data in that partition?

---

### Post by Bashing-om on 2012-09-19
guys, I am back in time for all to quit for the eve. Took me some time to get caught up on this thread. Looking good .... Thanks to old fred !

 I have to be out of town tomorrow so will be later in the eve before I can get back on this.

[INDENT]my regards and respect ............BDQ
  
[/INDENT]

---

### Post by sfourie on 2012-09-20
Good evening old fred. (well good day)
I reformatted the disk if I remember correctly using nfts.
Before I copied os onto that disk (sda) it only use to be one partition. All my data was on the disk that I mounted via media. 
So to answer yes my data was on the windows partition, which used to be the old disk.

---

### Post by oldfred on 2012-09-20
If you have data and it was NTFS, testdisk can recover a backup partition boot sector. Be sure to choose the correct NTFS partition.

testdisk is in the repository so you can install it to Ubuntu or liveCD.


As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

Lots of detail, shows screens:
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

---

### Post by sfourie on 2012-09-27
Hi guys.
I tried Testdisk but it did not find any files.
I then ran photorec which retrieved most files.
I reinstalled Ubuntu on sdb
Thank you for all you support.

---

### Post by Bashing-om on 2012-09-27
You are quite welcome, even if I did not do much but watch the master at work !

I hope in retrospect you enjoyed the learning experience.

[INDENT]Happy ubuntu'n <==BDQ

[/INDENT]

---

