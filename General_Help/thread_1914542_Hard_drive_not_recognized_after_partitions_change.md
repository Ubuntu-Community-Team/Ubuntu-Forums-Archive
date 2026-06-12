---
title: "Hard drive not recognized after partitions change"
date: 2012-01-24
forum: General Help
---

### Post by enuff on 2012-01-24
Hello, 
I have 2 hard drives and both of them were divided into 2 partitions. Today I decided that I don't want my secondary hard drive divided so I merged the two partition (under Windows 7). Next, when Xubuntu booted it displayed:

keys:Continue to wait; or Press S to skip mounting or M for manual recovery

I waited for about 10mins, then hit S and it loaded. However, my second hard drive (now 1 partition) is not visible in the Thunar. 
How can I make Xubuntu see my 'new' hard drive?

---

### Post by LewisTM on 2012-01-24
It's likely that the identifiers on your partitions have changed because of the merge. You need to update them in your fstab file.

Can you post the outputs of the following commands?
```
cat /etc/fstab
sudo fdisk -l
sudo blkid
```

---

### Post by enuff on 2012-01-24
Here it is 

```
martin@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sda2	/host	fuseblk	defaults,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096	0	0
/dev/sdb1	/media/7A8CBF588CBF0E1F	ntfs-3g	defaults,nosuid,nodev,locale=en_US.UTF-8	0	0
/dev/sda1	/media/sda1	ntfs	defaults,nls=utf8,umask=0222	0	0
/dev/sdb5	/media/131C218F60A28631	ntfs	defaults,nls=utf8,umask=0222,nosuid,nodev	0	0
/host/ubuntu/disks/root.disk	/	ext4	loop,errors=remount-ro	0	1
/host/ubuntu/disks/swap.disk	none	swap	loop,sw	0	0

```

```
martin@ubuntu:~$ sudo fdisk -l
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x18f22d7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40965749    20482843+   7  HPFS/NTFS/exFAT
/dev/sda2        40965750   234436544    96735397+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4917d2b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   488392064   244196001    7  HPFS/NTFS/exFAT
```

```
martin@ubuntu:~$ sudo blkid
/dev/loop0: UUID="2ec529b8-ed4f-4ae3-ab7f-fd8be68478f1" TYPE="ext4" 
/dev/sda1: UUID="B896C0CF96C08F76" TYPE="ntfs" 
/dev/sda2: UUID="485027A3502796AA" TYPE="ntfs" 
/dev/sdb1: UUID="7A8CBF588CBF0E1F" TYPE="ntfs"
```

The 250GB hard drive is the one that I merged the partitions.

---

### Post by LewisTM on 2012-01-24
I see you are running a Wubi installation.
You can certainly remove the /dev/sdb5 entry in your fstab since its now gone.

It's possible your /dev/sdb1 NTFS drive need to be checked and marked 'clean' for it to be mounted. Better do that in Windows.

If the problem persists you should post the terminal output of 
```
sudo mount /dev/sdb1
dmesg |tail # if the mount command fails
```

Cheers!

---

### Post by enuff on 2012-01-24
Yes, I forgot to mention about the Wubi. 
Removing /dev/sdb5 entry solved the problem with booting and "keys:Continue to wait; or Press S to skip mounting or M for manual recovery" is no longer displayed. 
However, I still don't see my 250GB hard drive in the side panel in Thunar. I have to go to media/sda1/ to access the files. 
I am now sure I understand that:
> It's possible your /dev/sdb1 NTFS drive need to be checked and marked 'clean' for it to be mounted. Better do that in Windows.

What should I do in Windows?

P.S. - the second partition of the other hard drive is also not present in Thunar. Now I see only the partition on which Wubi is installed. I used to have a list with partitions on the left panel of Thunar starting with File System and then 90GB partition, 40GB partition, 210GB partition, etc. Now I only have File System.

---

### Post by LewisTM on 2012-01-24
You just run a disk check on the 250 gb disk in Windows.
I'm saying that because Linux has a way of rejecting ntfs drives that are not marked 'clean', sometimes because of a power outage or any other interruption. A check fixes that.

And please provide the mount output. I assume of course that your /media/7A8CBF588CBF0E1F directory is empty at the moment i.e. the mount fails. The drive may not show up in Thunar but still be available. It would be the simplest explanation.

---

### Post by enuff on 2012-01-24
The directory /media/7A8CBF588CBF0E1F is not empty - all the files of the 250GB are there. Now I realized that I have misled you in my previous post. The content of media/sda1/ is actually one of the partitions of the other hard drive. 

Now I guess what I am trying to accomplish is to have 'media/sda1/' and '/media/7A8CBF588CBF0E1F' show as partition (icons) in Thunar's panel and on the desktop. 

Btw, is there any way that I can reset the hard drive configuration so next time when Xubuntu boots is detects everything the way it did the first time after I installed it?

---

### Post by LewisTM on 2012-01-24
The way Thunar manages partitions is different depending on how they were presented to Linux at boot.

If they are in fstab, they will be treated as static 'branches' that sit somewhere in your filesystem (could be in /media or anywhere else you choose). They will not be found on the right pane of Thunar. A debatable but consistent behavior. 

If they are not in fstab, they are considered "Hot Pluggable" and will show in the right pane and on the desktop. None of their contents will be available at bootup and your will have to manually open them to trigger a mount.

To see them that way, just remove /dev/sdb1 and /dev/sda1 from fstab.

---

### Post by enuff on 2012-01-24
Thanks, I removed /dev/sdb1 and /dev/sda1 from fstab and now everything is the way it used to be. 
I believe NTFS Configuration Tool, which I tired to use to make my 250GB drive auto-mount added the drives to fstab on first place.
Anyway, I am happy that now everything is back to normal and I will deal with the auto-mounting separately. 
Thanks for the help once again.

---

