---
title: "One windows NTFS drive not showing in 'locations'"
date: 2009-07-27
forum: General Help
---

### Post by starbase1 on 2009-07-27
I have Ubuntu 9.04, 64 bit,  installed on a system with 4 big (physical) NTFS drives, each 1 Tb.

The first one is split into two partitions, (One for Vista 64, one for XP 64).

When I look in 'Locations' I can see all the above partitions, except for the second hard drive, called logically enough, disk 2.

I went back to windows, and used the disk check utility, in case there was an error on it, but that made no differerence.

I have no idea why everything should work except this one drive - can anyone suggest something I could try to make it visible to Ubuntu?

---

### Post by merlinus on 2009-07-27
Is there an entry for it in /etc/fstab?

---

### Post by starbase1 on 2009-07-28
I think so... If the numbering is in sequence anyway!

I noticed that the one I think is it, sdb1, had different text in that file, so I brought it into line with the others.

I rebooted, but it still did not show under locations. Here's the text from the file:

/dev/sdd1                     /media/sdd1     ntfs         defaults                    0  0  
/dev/sdc1                     /media/sdc1     ntfs         nls=iso8859-1,ro,umask=000  0  0  
/dev/sdb1                     /media/sdb1     ntfs         nls=iso8859-1,ro,umask=000  0  0  
/dev/sda1                     /media/sda1     ntfs         nls=iso8859-1,ro,umask=000  0  0  
/dev/sda2                     /media/sda2     ntfs         nls=iso8859-1,ro,umask=000  0  0  

Any ideas?
Nick

---

### Post by merlinus on 2009-07-28
Did you look in the /media folder?  Also, which of these is the missing one (e.g. sdb1)?

---

### Post by starbase1 on 2009-07-29
OK, I found the media folder, the sdxx folders were all there.

I'm fairly sure it is sdb1, not least because unlike the others, when I open it the folder is empty.

I looked at the properties, and the thing that I notice is that the volume is "unknown". 

(The disk is good under windows)
Nick

---

### Post by nikhilk on 2009-07-29
> **starbase1 said:**
> OK, I found the media folder, the sdxx folders were all there.

I'm fairly sure it is sdb1, not least because unlike the others, when I open it the folder is empty.

It seems that the partition is not mounted, hence you are seeing an empty /media/sdb1 directory.
See if manual mounting works (or at least gives some error that will help)

First ensure /media/sdb1 is not mounted
```
sudo umount /media/sdb1
```
You will get a message like this "umount: /media/sdb1: not mounted"

Then mount it
```
sudo mount /media/sdb1
```

---

### Post by starbase1 on 2009-07-29
OK,I tried that:

nick@ubuntu:~$ sudo umount /media/sdb1
umount: /media/sdb1: not mounted
nick@ubuntu:~$ sudo mount /media/sdb1
fuse: mount failed: Device or resource busy
nick@ubuntu:~$ 

As you can see, it seems to think the device is busy...
Thanks, Nick

---

### Post by Hobgoblin on 2009-07-29
Can you post the output of...

```
df
```

and

```
fdisk -l
```

Also, can you post your entire /etc/fstab file.

---

### Post by starbase1 on 2009-07-29
nick@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                      29979608   6683868  21772848  24% /
tmpfs                  6076564         0   6076564   0% /lib/init/rw
varrun                 6076564       108   6076456   1% /var/run
varlock                6076564         0   6076564   0% /var/lock
udev                   6076564       176   6076388   1% /dev
tmpfs                  6076564       148   6076416   1% /dev/shm
/dev/sdb1            976759804 474826516 501933288  49% /host
lrm                    6076564      2560   6074004   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sdd1            976759804 229744372 747015432  24% /media/sdd1
/dev/sdc1            976759804 691497280 285262524  71% /media/sdc1
/dev/sda1            488384000 309128688 179255312  64% /media/sda1
/dev/sda2            488376316  56057688 432318628  12% /media/sda2
nick@ubuntu:~$


fdisk -l
returns nothing




# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                          /proc           proc         defaults                    0  0  
/host/ubuntu/disks/root.disk  /               ext3         loop,errors=remount-ro      0  1  
/host/ubuntu/disks/boot       /boot           none         bind                        0  0  
/host/ubuntu/disks/swap.disk  none            swap         loop,sw                     0  0  
/dev/scd0                     /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/scd1                     /media/cdrom1   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                      /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sdd1                     /media/sdd1     ntfs         defaults                    0  0  
/dev/sdc1                     /media/sdc1     ntfs         nls=iso8859-1,ro,umask=000  0  0  
/dev/sdb1                     /media/sdb1     ntfs         nls=iso8859-1,ro,umask=000  0  0  
/dev/sda1                     /media/sda1     ntfs         nls=iso8859-1,ro,umask=000  0  0  
/dev/sda2                     /media/sda2     ntfs         nls=iso8859-1,ro,umask=000  0  0

---

### Post by nikhilk on 2009-07-29
> **starbase1 said:**
> fdisk -l
returns nothing

The should have been run as
```
sudo fdisk -l
```

See if you have the latest versions of both ntfs-3g and fuse-utils, if not update them and see if that works. This is a shot in the dark but probably worth trying as it should be harmless.

---

### Post by starbase1 on 2009-07-29
> **nikhilk said:**
> The should have been run as
```
sudo fdisk -l
```

See if you have the latest versions of both ntfs-3g and fuse-utils, if not update them and see if that works. This is a shot in the dark but probably worth trying as it should be harmless.

I'm at the day job now, but I will try it when I get home.

Thanks for the help!
Nick

---

### Post by Hobgoblin on 2009-07-29
> **nikhilk said:**
> The should have been run as
```
sudo fdisk -l
```


Ooops, sorry.

---

### Post by starbase1 on 2009-07-29
ick@ubuntu:~$ sudo fdisk -l
[sudo] password for nick: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8163992

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS
/dev/sda2           60802      121602   488376320    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01256872

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa23cbc7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa23cbc72

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121602   976759808    7  HPFS/NTFS
nick@ubuntu:~$

---

### Post by starbase1 on 2009-07-29
> **nikhilk said:**
> See if you have the latest versions of both ntfs-3g and fuse-utils, if not update them and see if that works. 

How do I do that? I looked in add/remove but those were not there. I have been accepting all requests to update stuff.

Nick

---

### Post by nikhilk on 2009-07-30
> **starbase1 said:**
> How do I do that? I looked in add/remove but those were not there. I have been accepting all requests to update stuff.

Search for ntfs and fuse in Synaptic and confirm that they are installed and up-to-date (which they probably are since you are accepting all updates)

Post back output of
```
sudo cat /proc/mounts
```

I just want to confirm that the device /dev/sdb1 is not already mounted somewhere else since fuse thinks the device is busy.

---

### Post by starbase1 on 2009-07-30
OK, ntfsprogs had an ubuntu symbol, but no tick, libntfs10 too, so I am applying them now.

Lots of fuse stuff, I ticked the ones with an ubuntu symbol that were not marked, and the ones with a green box I marked for re-installation, on the basis it might help!

I've not used this stuff before, but it seems impressively easy - I like the way it knows the dependencies to keep things consistent!

Now to hit the big red button...

Nick

---

### Post by starbase1 on 2009-07-30
Output of cat:

nick@ubuntu:~$ sudo cat /proc/mounts
[sudo] password for nick: 
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw,mode=755 0 0
/dev/sdb1 /host fuseblk rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 0 0
/dev/loop0 / ext3 rw,errors=remount-ro,data=ordered 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=755 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
varrun /var/run tmpfs rw,nosuid,mode=755 0 0
varlock /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.28-14-generic/volatile tmpfs rw,mode=755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,nosuid,noexec,gid=5,mode=620 0 0
/dev/sdb1 /boot fuseblk rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 0 0
/dev/sdd1 /media/sdd1 fuseblk rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 0 0
/dev/sdc1 /media/sdc1 fuseblk ro,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 0 0
/dev/sda1 /media/sda1 fuseblk ro,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 0 0
/dev/sda2 /media/sda2 fuseblk ro,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec 0 0
gvfs-fuse-daemon /home/nick/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user_id=1000,group_id=1000 0 0
nick@ubuntu:~$ 



I notice that the sdb1 device does appear early in the list with different parameters,but I'm not sure what they mean...

I'm still hoping for direct help! But where would I go to look up what these parameters mean, for future reference?

Thanks,
Nick

---

### Post by nikhilk on 2009-07-31
Ok, it seems that you have installed Ubuntu via WUBI, is that correct? I have never done a WUBI install so my knowledge is limited in that regard.

> **starbase1 said:**
> /dev/sdb1 /host fuseblk rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 0 0

> **starbase1 said:**
> /dev/sdb1 /boot fuseblk rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 0 0

The /dev/sdb1 device as seen above is mounted twice, I do not know how is that possible! There is something I do not understand here.

> **starbase1 said:**
> I'm still hoping for direct help! But where would I go to look up what these parameters mean, for future reference?

Check [this]("http://www.mjmwired.net/kernel/Documentation/filesystems/fuse.txt") link for description of the fuse mount options.

---

### Post by starbase1 on 2009-07-31
> **nikhilk said:**
> Ok, it seems that you have installed Ubuntu via WUBI, is that correct? I have never done a WUBI install so my knowledge is limited in that regard.





The /dev/sdb1 device as seen above is mounted twice, I do not know how is that possible! There is something I do not understand here.



Check [this]("http://www.mjmwired.net/kernel/Documentation/filesystems/fuse.txt") link for description of the fuse mount options.

Yes, I like Wubi as I get nervous about partitioning hard drives!

From what you say, the obvious thing to do is to unmount it, (twice if necessary?), and then start again?

Thanks,
Nick

---

### Post by nikhilk on 2009-07-31
> **starbase1 said:**
> Yes, I like Wubi as I get nervous about partitioning hard drives!

From what you say, the obvious thing to do is to unmount it, (twice if necessary?), and then start again?

Thanks,
Nick

I am not sure. I am not able to understand why it is mounted as /host and /boot in the first place. But I guess you can try that and see how it goes.

---

### Post by starbase1 on 2009-07-31
OK, I've posted a question over in the install area, to check if it might be something Wubi needs. It would be a shame to break the whole install when I have got it so close to what I need!

Thanks again,
Nick

---

