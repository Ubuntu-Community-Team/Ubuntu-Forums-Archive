---
title: "problem booting"
date: 2009-07-30
forum: General Help
---

### Post by cycrosism on 2009-07-30
I tried to run a .rar file then shortly later it crashed my computer and I couldn't move my mouse or anything so I did a restart by clicking the reset button. Now when I try to boot I get the following errors

Mounting sys on /root/sys failed
Mounting proc on /root/Proc failed
Target filesystem doesn't have a /sbin/init
No init found

I have tried doing numerous things in the terminal to fix this such as 

```

ubuntu@ubuntu:~$ sudo fsck /dev/sdc1/
fsck.ext2: Not a directory while trying to open /dev/sdc1/

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

That failed so I tried 

```
ubuntu@ubuntu:~$ sudo e2fsck -b 8193 /dev/sdc1/
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Not a directory while trying to open /dev/sdc1/

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

Any thoughts?

---

### Post by wojox on 2009-07-30
Try running your live cd. Open a terminal, make sure the root partition is unmounted and run fsck.

---

### Post by cycrosism on 2009-07-30
I am on the live CD at the moment. How do I unmount it?

---

### Post by MichealH on 2009-07-30
I think if you go to Computer you see File System and Right click then Unmount!

---

### Post by cycrosism on 2009-07-30
Well I am going to assume it is already unmounted as when I right click on that drive it only says "Mount Volume". What do I do from here?

---

### Post by MichealH on 2009-07-30
Open Terminal and type "fsck" without quotes.

---

### Post by cycrosism on 2009-07-30
```
ubuntu@ubuntu:~$ fsck
fsck 1.41.4 (27-Jan-2009)
ubuntu@ubuntu:~$ 

```I do not think much happened

edit - I can't mount the drive either, it says "Cannot mount volume." mount: wrong fs tpye, bad option, bad superblock on /dev/sdc1, etc etc...

---

### Post by cycrosism on 2009-07-30
```
ubuntu@ubuntu:~$ sudo fsck /dev/sdc1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sdc1: recovering journal
/dev/sdc1: Attempt to read block from filesystem resulted in short read while reading block 9326063

JBD: Failed to read block at offset 19417
fsck.ext3: Input/output error while recovering ext3 journal of /dev/sdc1
ubuntu@ubuntu:~$ 

```

That's the error I got when i tried sudo fsck /dev/sdc1/ and yes it is unmounted

---

### Post by MichealH on 2009-07-30
Do you know the partition like /dev/sda then the number that goes after or are you taking all your drive because I typed it into my terminal and it had went to my mounted volume but i also tried out this command (My ubunu is /dev/sda3 so i tried):
```
fsdk /dev/sda3
```
and i gave me this:
```
fsck /dev/sda3
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda3 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.

``` 
but think if you are doing your complete drive type:
```
fsck /dev/sda1
```

---

### Post by cycrosism on 2009-07-30
Oh, this might be helpful:

```
Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c3d9a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9327    74919096   83  Linux
/dev/sdc2            9328        9729     3229065    5  Extended
/dev/sdc5            9328        9729     3229033+  82  Linux swap / Solaris

```edit - I think I fixed the problem,

```
ubuntu@ubuntu:~$ sudo fsck /dev/sdc1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sdc1: recovering journal
Clearing orphaned inode 1802248 (uid=113, gid=123, mode=0100600, size=0)
Clearing orphaned inode 1802247 (uid=113, gid=123, mode=0100600, size=0)
Clearing orphaned inode 1802246 (uid=113, gid=123, mode=0100600, size=0)
Clearing orphaned inode 1802245 (uid=113, gid=123, mode=0100600, size=0)
Clearing orphaned inode 1802244 (uid=113, gid=123, mode=0100600, size=0)
/dev/sdc1: clean, 570007/4685824 files, 11736051/18729774 blocks
ubuntu@ubuntu:~$ 

```I will try to boot normally and if it works I will post here stating so. Thanks for the help :)

---

### Post by MichealH on 2009-07-30
> **cycrosism said:**
> ```
ubuntu@ubuntu:~$ sudo fsck /dev/sdc1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sdc1: recovering journal
/dev/sdc1: Attempt to read block from filesystem resulted in short read while reading block 9326063

JBD: Failed to read block at offset 19417
fsck.ext3: Input/output error while recovering ext3 journal of /dev/sdc1
ubuntu@ubuntu:~$ 

```That's the error I got when i tried sudo fsck /dev/sdc1/ and yes it is unmounted

Is your partition sdc1 because mine is sda not sdc

---

### Post by cycrosism on 2009-07-30
Problem solved, I was able to successfully boot this time. Thanks :)

---

### Post by MichealH on 2009-07-30
> **cycrosism said:**
> Oh, this might be helpful:

```
Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c3d9a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9327    74919096   83  Linux
/dev/sdc2            9328        9729     3229065    5  Extended
/dev/sdc5            9328        9729     3229033+  82  Linux swap / Solaris

```edit - I think I fixed the problem,

```
ubuntu@ubuntu:~$ sudo fsck /dev/sdc1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sdc1: recovering journal
Clearing orphaned inode 1802248 (uid=113, gid=123, mode=0100600, size=0)
Clearing orphaned inode 1802247 (uid=113, gid=123, mode=0100600, size=0)
Clearing orphaned inode 1802246 (uid=113, gid=123, mode=0100600, size=0)
Clearing orphaned inode 1802245 (uid=113, gid=123, mode=0100600, size=0)
Clearing orphaned inode 1802244 (uid=113, gid=123, mode=0100600, size=0)
/dev/sdc1: clean, 570007/4685824 files, 11736051/18729774 blocks
ubuntu@ubuntu:~$ 

```I will try to boot normally and if it works I will post here stating so. Thanks for the help :)
Always happy to help:D

EDIT - Dont forget to mark this SOLVED

---

