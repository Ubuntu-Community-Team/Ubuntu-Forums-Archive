---
title: "how to solve partition mounting problem"
date: 2006-05-13
forum: General Help
---

### Post by 1002285 on 2006-05-13
Hi,
I'll see if anyone here will point me in the right direction in solving my filesystem problem.

I have a dual-boot computer here with 2 hard disks. Windows is the main OS here and it is on a separate bigger, newer harddisk with NTFS file system. On the other hard disk I installed Ubuntu 5.10 and also made a FAT32 partition that could be used from both OS-s (10 GB ubuntu and 10 GB FAT32).
But neither Windows nor Ubuntu can see this partition. I think I have tried all the usual methods for mounting, and as I have solved the same problem on another computer without too much effort, I think there is something else wrong here.
And I really think I did the partitioning step right during the installation - it was not the first time I made a Windows-Ubuntu dual-boot system.
Ubuntu says (after all mounting steps I've tried) at the boot that "mounting local filesystems" failed.
Windows shows me local disk C: in "my computer" (and yes, it is C: where Ubuntu is, Windows is on F:), but it will not show any contents of the partition, saying that it is not formatted. I haven't tried formatting it from Windows after installing Ubuntu, because I am afraid it might delete Ubuntu and I thought there might be a better, safer way.
I do remember that I tried formatting this disk from Windows before installing Ubuntu and Windows said "Windows cannot format this disk".
Are there any partitioning applications that could help me here or should I try partitioning using Ubuntu 5.10 install or live CD?

---

### Post by aysiu on 2006-05-13
In Windows, go to the Disk Management. I think it's either in the Control Panel or in All Programs under Accessories > System Tools. Poke around--you'll find it eventually.

Once you get to Disk Management, you'll see all the partitions. Re-format the FAT32 partition as FAT32 *again*. Make sure Windows can see this partition okay after the format.

Then boot into Ubuntu and follow these instructions to get it mounted (yes, it starts off with NTFS as an example, but then it goes on to talk about FAT32): [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by 1002285 on 2006-05-13
Thanks, I think I'll start trying right away.

---

### Post by 1002285 on 2006-05-13
Hmm,
I followed the instructions you pointed me to, and discovered that I can use NTFS too (didnt know that). And I edited FSTAB and got the NTFS partition actually working, but not the FAT32 one.
Maybe this is an interesting result after typing sudo mount -a. I didn't do it before, but now, after the reboot and failing to mount the partition, I typed this in.
And the result is
"
mount: unknown filesystem type 'umask=000'
"
Does this mean anything interesting here?
I did change the fstab file right, I think
(I copied the line for the FAT32 I copied from the instructions and changed according to my folder name).

---

### Post by aysiu on 2006-05-13
[QUOTE=1002285]
mount: unknown filesystem type 'umask=000'
Does this mean anything interesting here?
I did change the fstab file right, I think
(I copied the line for the FAT32 I copied from the instructions and changed according to my folder name).[/QUOTE] Can you post the output of this command? ```
cat /etc/fstab
```

---

### Post by 1002285 on 2006-05-16
[QUOTE=aysiu]Can you post the output of this command? ```
cat /etc/fstab
```[/QUOTE]

(strange - I don't think I got a notification about a new answer to the thread, I only checked now and here was your answer).
So here's the output of the command:
/dev/hda1 /media/windows_NTFS_partition ntfs nls=utf8, umask=o222 0 0
/dev/hdb2 / ext3 defaults,errors=remount-ro 0 1
/dev/hdb6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,usernoauto 0 0
/dev/hdb5/ /media/FAT32 iocharset=utf8,umask=000 0 0

And I found it strange that there was another / in the line starting /def/hdb5/ 
I changed it but the result was the same. Does it matter if the / is there or not?

---

### Post by KillrBuckeye on 2006-05-16
[QUOTE=1002285]
/dev/hda1 /media/windows_NTFS_partition ntfs nls=utf8, umask=o222 0 0
/dev/hdb2 / ext3 defaults,errors=remount-ro 0 1
/dev/hdb6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,usernoauto 0 0
/dev/hdb5/ /media/FAT32 iocharset=utf8,umask=000 0 0
[/QUOTE]

Each line of the fstab lists:  device, mount point, file system, options, and permissions (I think).  Notice that each line in the FSTAB seems to have complete information *except* your FAT32 line, which is missing a file system entry!  Ubuntu probably failed to recognize the file system on the FAT32 partition because something went wrong the first time you tried to create and format that partition.  If you sucessfully reformatted the FAT32 partition and it is being recognized within Windows, you probably just need to change the FAT32 line to this:

/dev/hdb5 /media/FAT32 vfat iocharset=utf8,umask=000 0 0

So just add the "vfat" for filesystem type and try to manually mount, or just reboot.  TBH I'm not sure what the "iocharset" option is, but you can probably just leave that as is.  Hope this works!

---

### Post by aysiu on 2006-05-16
First of all, I would mount both Windows partitions in their own directories instead of within the /media or /mnt directories. Sometimes that can make them behave strangely, but that's not the problem.

[QUOTE=1002285]
/dev/hda1 /media/windows_NTFS_partition ntfs nls=utf8, umask=o222 0 0[/quote] Here's one problem. It looks as if you typed ```
nls=utf8 umask=o222
``` That should read ```
nls=utf8,umask=0222
``` > /dev/hdb5/ /media/FAT32 iocharset=utf8,umask=000 0 0 You seem to have left off the filesystem type here. This line should read: ```
/dev/hdb5 /media/FAT32 vfat iocharset=utf8,umask=000 0 0
```

---

### Post by 1002285 on 2006-05-16
Thanks to both of you, I had really made the FAT system's line wrong.
But with the NTFS partition I only typed it wrong here - it was working already before.

But can you look at this thread, too - this is about another computer where I upgraded to Dapper Beta and lost PCMCIA LAN card:
[http://www.ubuntuforums.org/showthread.php?p=1022722#post1022722](http://www.ubuntuforums.org/showthread.php?p=1022722#post1022722)

I do understand that if there's no answer then probably maybe really knows the answer, but it doesn't seem too difficult for experienced users.

---

### Post by 1002285 on 2006-05-16
Thanks to both of you, I had really made the FAT system's line wrong.
But with the NTFS partition I only typed it wrong here - it was working already before.

But can you look at this thread, too - this is about another computer where I upgraded to Dapper Beta and lost PCMCIA LAN card:
[http://www.ubuntuforums.org/showthread.php?p=1022722#post1022722](http://www.ubuntuforums.org/showthread.php?p=1022722#post1022722)

I do understand that if there's no answer then probably maybe really knows the answer, but it doesn't seem too difficult for experienced users.

---

### Post by 1002285 on 2006-05-16
Thanks to both of you, I had really made the FAT system's line wrong.
But with the NTFS partition I only typed it wrong here - it was working already before.

But can you look at this thread, too - this is about another computer where I upgraded to Dapper Beta and lost PCMCIA LAN card:
[http://www.ubuntuforums.org/showthread.php?p=1022722#post1022722](http://www.ubuntuforums.org/showthread.php?p=1022722#post1022722)

I do understand that if there's no answer then probably maybe really knows the answer, but it doesn't seem too difficult for experienced users.

---

