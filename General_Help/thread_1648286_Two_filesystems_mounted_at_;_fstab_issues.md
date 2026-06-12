---
title: "Two filesystems mounted at /; fstab issues"
date: 2010-12-18
forum: General Help
---

### Post by cscj01 on 2010-12-18
I have a 500 GB fixed drive partitioned with XP, Ubuntu 10.10 x64, and Swap. I also have a 500 GB USB drive that I use to clone the fixed drive using Clonezilla for a backup. I labeled the first two USB partitions as Win_XP and Ubuntu respectively. I suppose the correct terminology is that I labeled the respective filesystems as shown. There are no partition labels.

If I check the mount points using gparted or Disk Utility, I see that the Win_XP partition on the USB drive is mounted at /media/Win_XP, and the Ubuntu partition on the USB drive is mounted at /. So, the Ubuntu partition on the USB drive is being auto-mounted at / rather than at /media/Ubuntu, which is where I understand auto-mounted USB partitions should be mounted. The fixed disk partitions are being mounted at /media/sda1 and at / respectively. So, I have two file systems mounted at /.

I tried to unmount the USB Ubuntu partition using GParted, but I get an error message that says

> Could not unmount /dev/sdc2

The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually.

How do I correct this? I tried "sudo /dev/sdc2" but got the message "umount: /dev/sdc2: not mounted".

Here is my fstab for further information:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdc2 :
UUID=b61632e9-7186-4ec9-9e4c-214c01d39a4e	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdb1 :
UUID=709849C898498E12	/media/Data	ntfs-3g	defaults,nosuid,nodev,locale=en_US.UTF-8	0	0
#Entry for /dev/sda1 :
UUID=C48C88E98C88D6F8	/media/sda1	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
/dev/sdd1	/media/C48C88E98C88D6F8__	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177	0	0
UUID=17A5-7B95	/media/C48C88E98C88D6F8	ntfs-3g	defaults,nosuid,nodev,locale=en_US.UTF-8	0	0
#Entry for /dev/sdc3 :
UUID=5b3c361f-14a1-45fa-bd52-49cfae3f331b	none	swap	sw	0	0
#Entry for /dev/sdc3 :
UUID=5b3c361f-14a1-45fa-bd52-49cfae3f331b	none	swap	sw	0	0
//cp2/g	/mnt/cp2	smbfs	iocharset=utf8,uid=1000	0	0
/dev/sdd1 is a USB stick that is not present, and the mount points assosiated with it are the ones for which I get the messages at boot. Could this be part of my problem for which I initially posted?

---

### Post by Morbius1 on 2010-12-18
This is close to the end of the day for me so I don't know if I can take you out of this but you've got a bit of a mess there in your fstab:

> UUID=[COLOR=Blue]C48C88E98C88D6F8[/COLOR]    /media/sda1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
/dev/sdd1    /media/[COLOR=Blue]C48C88E98C88D6F8__[/COLOR]    ntfs    defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=  1000,dmask=0077,fmask=0177    0    0
UUID=17A5-7B95    /media/[COLOR=Blue]C48C88E98C88D6F8[/COLOR]    ntfs-3g    defaults,nosuid,nodev,locale=en_US.UTF-8    0    0It looks like you're trying to mount the same partition multiple times,  using UUID twice and again using /dev/sdxy. I would comment them all out by placing a "#" sign in front of each line so that they look like this:
> [COLOR=Red]**#**[/COLOR]UUID=[COLOR=Black]C48C88E98C88D6F8[/COLOR]    /media/sda1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
 **[COLOR=Red]#[/COLOR]**/dev/sdd1    /media/[COLOR=Blue][COLOR=Black]C48C88E98C88D6F8[/COLOR]__[/COLOR]    ntfs    defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=  1000,dmask=0077,fmask=0177    0    0
**[COLOR=Red]#[/COLOR]**UUID=17A5-7B95    /media/C48C88E98C88D6F8    ntfs-3g    defaults,nosuid,nodev,locale=en_US.UTF-8    0    0On the last one UUID=17A5-7B95 is the UUID of a FAT32 partition not an NTFS partition so I'm not sure what's going on there.

Once you make those changes to fstab remove the external USB devices and plug them in again and wait for the system to mount them by itself. Then post the output of the following command so we can all see how your partitions are set up:
```
sudo blkid -c /dev/null
```

---

### Post by oldfred on 2010-12-18
Because you cloned drive, it is seeing the same UUID on both the original and the copy. A clone is not intended as a backup, except that you would disconnect it and save it. But would be directly bootable as everything is the same.

But a standard backup will not have the same UUIDs but then cannot be directly booted if that  is your intent. Grub would have to be reinstalled and fstab updated.

---

### Post by cscj01 on 2010-12-18
> **Morbius1 said:**
> This is close to the end of the day for me so I don't know if I can take you out of this but you've got a bit of a mess there in your fstab:

It looks like you're trying to mount the same partition multiple times,  using UUID twice and again using /dev/sdxy. I would comment them all out by placing a "#" sign in front of each line so that they look like this:
On the last one UUID=17A5-7B95 is the UUID of a FAT32 partition not an NTFS partition so I'm not sure what's going on there.

Once you make those changes to fstab remove the external USB devices and plug them in again and wait for the system to mount them by itself. Then post the output of the following command so we can all see how your partitions are set up:
```
sudo blkid -c /dev/null
```

Here's the output:

> /dev/sda1: UUID="C48C88E98C88D6F8" TYPE="ntfs" 
/dev/sda2: UUID="b61632e9-7186-4ec9-9e4c-214c01d39a4e" TYPE="ext4" 
/dev/sda3: UUID="5b3c361f-14a1-45fa-bd52-49cfae3f331b" TYPE="swap" 
/dev/sdb1: LABEL="Data" UUID="709849C898498E12" TYPE="ntfs" 
/dev/sdc1: LABEL="Win_XP" UUID="C48C88E98C88D6F8" TYPE="ntfs" 
/dev/sdc2: LABEL="Ubuntu" UUID="b61632e9-7186-4ec9-9e4c-214c01d39a4e" TYPE="ext4" 
/dev/sdc3: UUID="5b3c361f-14a1-45fa-bd52-49cfae3f331b" TYPE="swap"

---

### Post by cscj01 on 2010-12-18
> **oldfred said:**
> Because you cloned drive, it is seeing the same UUID on both the original and the copy. A clone is not intended as a backup, except that you would disconnect it and save it. But would be directly bootable as everything is the same.

But a standard backup will not have the same UUIDs but then cannot be directly booted if that  is your intent. Grub would have to be reinstalled and fstab updated.

I have been doing this since 9.04.  I have never had this problem until 10.10.  I suppose things must have changed as to how drives are handled.  But I understand your point.

---

### Post by oldfred on 2010-12-18
They changed fstab from drive, partition (/dev/sda1)  to UUIDs as UUIDs are unique, except in your case.

You can change back to mounting by drive, partition or possibly  use labels to mount partitions in fstab. But I do not know if the clone will also copy labels?

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by Morbius1 on 2010-12-19
Yikes !
```
I have a 500 GB fixed drive partitioned with XP, Ubuntu 10.10 x64, and Swap.
```Yet the only reference to that disk ( which I assume is sda ) in fstab is this:
> #Entry for /dev/sda1 :
UUID=C48C88E98C88D6F8    /media/sda1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
What I should be seeing in fstab is something like this:
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc nodev,noexec,nosuid 0 0
#Entry for /dev/sda1 :
UUID=C48C88E98C88D6F8 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 0
#Entry for /dev/sda2 :
UUID=b61632e9-7186-4ec9-9e4c-214c01d39a4e / ext4 errors=remount-ro 0 1
#Entry for /dev/sda3 :
UUID=5b3c361f-14a1-45fa-bd52-49cfae3f331b none swap sw 0 0Normally I would suggest that you make a backup copy of your current fstab, remove every reference to anything other that sda in the original, and make the original look like the above. But for the life of me I don't know how you are even able to boot into this box so there's something I'm obviously missing here.

---

### Post by oldfred on 2010-12-19
I think using a sda1 as the mount point in fstab adds to confusion.  Because the UUID is both sda1 & sdc1. 


From fstab:
```
UUID=[COLOR=Red]C48C88E98C88D6F8[/COLOR] /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

From blkid:
```
/dev/sda1: UUID="[COLOR=Red]C48C88E98C88D6F8[/COLOR]" TYPE="ntfs"
/dev/sdc1: LABEL="Win_XP" UUID="[COLOR=Red]C48C88E98C88D6F8[/COLOR]" TYPE="ntfs"
```

Better in this case to use this style, so sda1 is sda1:
/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 0

---

### Post by cscj01 on 2010-12-19
> **oldfred said:**
> I think using a sda1 as the mount point in fstab adds to confusion.  Because the UUID is both sda1 & sdc1. 


From fstab:
```
UUID=[COLOR=Red]C48C88E98C88D6F8[/COLOR] /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

From blkid:
```
/dev/sda1: UUID="[COLOR=Red]C48C88E98C88D6F8[/COLOR]" TYPE="ntfs"
/dev/sdc1: LABEL="Win_XP" UUID="[COLOR=Red]C48C88E98C88D6F8[/COLOR]" TYPE="ntfs"
```

Better in this case to use this style, so sda1 is sda1:
/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 0

Okay, here's my fstab now:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdb1 :
UUID=709849C898498E12	/media/Data	ntfs-3g	defaults,nosuid,nodev,locale=en_US.UTF-8	0	0
#Entry for /dev/sda1 :
/dev/sda1	/media/sda1	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for Samba Share drive g on cp2
//cp2/g	/mnt/cp2	smbfs	iocharset=utf8,uid=1000	0	0

```

I have the following folders in /media:

[LIST=1]
[*] sda1 - contains my XP partition on the internal drive;
[*] Data - contains my data partition on the internal drive;
[*] Win_XP - contains my XP partition on the USB drive;
[*] Ubuntu - contains my Ubuntu filesystem on the USB drive;
[*] C48C88E98C88D6F8 - is empty.
[/LIST]
So Ubuntu is mounting the USB partitions using the filesystem labels and sda1 as sda1.

Thanks for all your help.

One more question.  If I upgrade to a new release, will I need to modify my fstab after the upgrade?  If so, I can save the old one before upgrade, but just making sure before 11.04 comes along.

---

### Post by oldfred on 2010-12-19
I always do new installs, so I try to save any files I manually edit in the system folders. I just copy them into a folder in /home as I backup /home (not as often as I should). At least then I can refer to them, but do not necessarily copy them back after a new install.

---

### Post by cscj01 on 2010-12-20
Thanks.  I'll mark this as solved.

---

