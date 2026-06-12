---
title: "/etc/fstab and setting permissions for external hard drive"
date: 2010-07-30
forum: General Help
---

### Post by rawlins02 on 2010-07-30
I have a new install of Lucid.  I typically allow an automount of an external hard drive. Despite using -p options, I'm finding that all of the files I rsync or scp to the drive are not having their permissions preserved.  Assume I need an entry in /etc/fstab.  Tried several options, but keep getting an error that only root can mount the drive, after this addition to /etc/fstab:

```

# for external Free Agent hard drive.
/dev/sdb1      /media/FreeAgentDrive	ntfs-3g	root,dmask=0022   0   0

```

> sudo fdisk -l

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2816    22611928+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            2817       18985   129877492+   5  Extended
/dev/sda5            2817        4274    11711353+  83  Linux
/dev/sda6            4275       17040   102542863+  83  Linux
/dev/sda7           17041       18256     9767488+  83  Linux
/dev/sda8           18257       18985     5855661   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfef64909

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS



```

---

### Post by davidmohammed on 2010-07-30
have you tried ntfs-config? - it automatically sets your /etc/fstab with the correct permissions to access ntfs drives.

---

### Post by Morbius1 on 2010-07-30
I may be missing something in the question.

You can't preserve ownership and permissions in a transfer of files to a windows filesystem because a windows filesystem has no ownership or permissions "bits" to set. You can set an mask in fstab ( uid=, gid=, umask= ) to mount a windows filesytem with a specific owner and permission but all subsequent adds will inherit those ownership and permissions settings.

[COLOR=Blue]EDIT: Can you create another partition on the external device formatted in ext2/3/4? Then you can preserve permissions.[/COLOR]

---

### Post by rawlins02 on 2010-07-30
Excellent. I've installed the package and rebooted with the drive hooked up. Here are the last two lines of df command

```

/dev/sdb1            976760000  39463872 937296128   5% /media/FreeAgent Drive
/dev/sda1             22611928  21649468    962460  96% /media/Preload

```


Seems to have mounted this new /media/Preload. Not sure what that is. Mouse perhaps.  Free Agent is my external drive that's previously been on /dev/sdb1.  This tool is probably simple to use, but any additional suggestions are much appreciated. Can't find the umask part.

---

### Post by prodigy_ on 2010-07-30
> **rawlins02 said:**
> ```
dmask=0022
```
This option will only affect directories. For files you need **fmask**, for example: ```
fmask=133
``` will result in -rw-r--r-- permissions.

Like **Morbius1** said, original ACLs will be lost when you copy files from ext to NTFS. You are, therefore, limited to [mount options that ntfs-3g supports](http://linux.die.net/man/8/mount.ntfs-3g). These options are partition-wide; **chown** and **chmod** commands will have no effect on files/directories that are on NTFS partitions.

---

### Post by rawlins02 on 2010-07-30
> 
You can't preserve ownership and permissions in a transfer of files to a windows filesystem because a windows filesystem has no ownership or permissions "bits" to set. You can set an mask in fstab ( uid=, gid=, umask= ) to mount a windows filesytem with a specific owner and permission but all subsequent adds will inherit those ownership and permissions settings.


EDIT: Can you create another partition on the external device formatted in ext2/3/4? Then you can preserve permissions.



What is the easiest way to format this drive if I delete all contents? Interestingly, I just got finish formatting another new machine dual boot Windows/linux. Used gparted on Live CD. Or is there something here on Karmic that will do this. Sorry for my lack of know-how.

---

### Post by CharlesA on 2010-07-30
If you are just formatting, you can use *sudo mkfs.ext3 /dev/sdb1* to create a ext3 file system and *sudo mkfs.ext4 /dev/sdb1* to create an ext4 file system.

Otherwise boot off a Ubuntu CD and use Gparted.

---

### Post by rawlins02 on 2010-07-30
Thanks folks. I'm going to use gparted to set up both ext3 and NTFS partitions on this 1TB drive.  This week has been all about partitions...:p

---

