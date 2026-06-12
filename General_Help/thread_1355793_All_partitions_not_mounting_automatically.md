---
title: "All partitions not mounting automatically"
date: 2009-12-15
forum: General Help
---

### Post by roonie on 2009-12-15
I've just recently installed Ubuntu 9.10 on my laptop, I have 2 ext4 partitions which have my Linux installation and all the other partitions are NTFS.

When I start Linux, There are certain partitions that load, while the others I have to manually mount. More specifically one of the ext partitions sda7 just stopped mounting automatically. I see only 3 partitions that mount when Ubuntu starts, while the others have to be manually mounted. 

I tried adding a > sudo mount /dev/sda7 /media/sda7 in the terminal to mount the ext4 partition.

I don't know what else to try, Is there any way that I can have all the drives mount automatically at start-up by adding a command to the Startup Applications?

Here is my fdisk -l info:
> 
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77777777

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       14592    96727365    f  W95 Ext'd (LBA)
/dev/sda5            2551        3885    10723356   83  Linux
/dev/sda6            3886        4007      979933+  82  Linux swap / Solaris
/dev/sda7            4008        5100     8779491   83  Linux
/dev/sda8            5101        7650    20482843+   7  HPFS/NTFS
/dev/sda9            7651       10200    20482843+   7  HPFS/NTFS
/dev/sda10          10201       12750    20482843+   7  HPFS/NTFS
/dev/sda11          12751       14592    14795833+   7  HPFS/NTFS

---

### Post by bhupinderjitbawa on 2009-12-15
just edit /etc/fstab and add enteries for ntfs paritions
follow this url to edit..
[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by Leppie on 2009-12-15
could you post your fstab?

---

### Post by roonie on 2009-12-20
@Leppie

proc                                       /proc          proc         defaults                 0  0  
# / was on /dev/sda5 during installation
UUID=f0136125-46f1-44eb-9fdf-04fd23d9bc33  /              ext4         errors=remount-ro        0  1  
# swap was on /dev/sda10 during installation
UUID=cfa92d1e-f028-4925-90c3-0f4048d9a0d5  none           swap         sw                       0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8    0  0  
/dev/sda1                                  /media/sda1    ntfs         nls=iso8859-1,umask=000  0  0  
/dev/sda6                                  /media/sda6    ntfs         nls=iso8859-1,umask=000  0  0  
/dev/sda7                                  /media/sda7    ntfs         nls=iso8859-1,umask=000  0  0  
/dev/sda8                                  /media/sda8    ntfs         nls=iso8859-1,umask=000  0  0  
/dev/sda9                                  /media/sda9    ntfs         nls=iso8859-1,umask=000  0  0  


@bhupinderjitbawa

Thanks, will try that.

---

### Post by dcstar on 2009-12-20
> **roonie said:**
> 
.........
I don't know what else to try, Is there any way that I can have all the drives mount automatically at start-up by adding a command to the Startup Applications?


Install the **pysdm** package and use that.

---

### Post by roonie on 2009-12-21
@dcstar

I've installed it and I followed the steps to do that but nothing worked.

I used the Storage Device Manager to check if the devices were set to mount at boot time. They were all set. 

I also removed the setting for Mount device in read-only mode but that setting keeps turning on.

---

### Post by vanadium on 2009-12-21
To see whether and what the error is in /etc/fstab, execute the command

```

sudo mount -a

```

If there is no output, all drives listed in /etc/fstab should be mounted and be accessible. Any output indicates an error. Post the output back here so we can see what it going on.

---

### Post by Some Penguin on 2009-12-21
You might want to decide whether it's ext4 (as per post 1, and is not implausible based on the fdisk as well), or ntfs (per the fstab in post 4).   What do you think happens when you list the incorrect filesystem type in /etc/fstab?

---

### Post by roonie on 2009-12-25
> **vanadium said:**
> To see whether and what the error is in /etc/fstab, execute the command

```

sudo mount -a

```

If there is no output, all drives listed in /etc/fstab should be mounted and be accessible. Any output indicates an error. Post the output back here so we can see what it going on.

OK there were a few errors

TFS signature is missing.
Failed to mount '/dev/sda6': Invalid argument
The device '/dev/sda6' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
NTFS signature is missing.
Failed to mount '/dev/sda7': Invalid argument
The device '/dev/sda7' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


sda7 is the file system. I have 2 linux partitions and the rest are NTFS ones

---

### Post by Morbius1 on 2009-12-25
It looks like there is only one more piece of information left to ask for:

Please post the output of the following command: **sudo blkid**

---

### Post by vanadium on 2009-12-25
The system tries to attach sda6 and sda7 as ntfs volumes. We could already have seen that from your previous posts. Remove both these lines from your /etc/fstab:

```

/dev/sda6 /media/sda6 ntfs nls=iso8859-1,umask=000 0 0
/dev/sda7 /media/sda7 ntfs nls=iso8859-1,umask=000 0 0

```

---

### Post by Morbius1 on 2009-12-25
> We could already have seen that from your previous posts.

Quite right. Sorry for the intrusion. Ignore my post:redface:

---

### Post by vanadium on 2009-12-25
Don't worry. I did not see it myself ;)

---

### Post by roonie on 2009-12-28
Alright, Ive removed the lines from /etc/fstab. fingers crossed

---

### Post by roonie on 2010-01-01
removing the lines had no effect. I tried creating folders in /media and then setting the mount points to /media/Apps instead of /media/sda6 but it still only mounts 3 partitions out of 6.

What should I do? :S

---

