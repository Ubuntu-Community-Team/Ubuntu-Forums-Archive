---
title: "lost ability to boot up"
date: 2012-04-07
forum: General Help
---

### Post by latestarter on 2012-04-07
Using my laptop with UBUNTU operating system whilst moving a file to Wastebin the screen froze (pointer changed hand and pointing finger)and nothing would open or close so I crashed the system and then tried to boot up, but on this occasion it is failing to boot up.

Error messages
Mount: mounting /dev/disk/by-uuid/57901173-89fe-4159-9be7-88afbeaf813f on /root
Failed: invalid argument
Mount: mounting/dev on /root/dev failed: no such file or directory
Mount: mounting/sys on /root/sys failed: no such file or directory
Mount: mounting/proc on /root/proc failed: no such file or directory
Target filesystem doesn't have a /sbin/init
No init foumd. try passing init= bootarg.

Any ideas?

---

### Post by Basher101 on 2012-04-07
pop in a live cd and try [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by latestarter on 2012-04-08
Thanks Basher, did that but now I have lost my 'grub', and laptop just try's to boot up on the original 'Vista'. I ran 'sudo fdisk -l' and came up with this-

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9c62b218

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         181     1453851    7  HPFS/NTFS
/dev/sda2   *       18310       18704     3166016    7  HPFS/NTFS
/dev/sda3           19255       19458     1626112    7  HPFS/NTFS
/dev/sda4             182       18309   145613160    5  Extended
/dev/sda5             182       12929   102398278+  83  Linux
/dev/sda6           17569       18309     5952051   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 

Any ideas about how to restore the 'grub'?

---

### Post by roelforg on 2012-04-08
Question:
does the uuid from the error match the one blkid generates?

---

### Post by latestarter on 2012-04-08
Thanks for the quick reply, running the sudo fdisk was about the limit of my knowledge (from a past problem), so not sure what you are asking.

---

### Post by roelforg on 2012-04-08
> **latestarter said:**
> Thanks for the quick reply, running the sudo fdisk was about the limit of my knowledge (from a past problem), so not sure what you are asking.

```

sudo blkid

```

---

### Post by latestarter on 2012-04-08
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="6422abcc-4d9c-413c-a1d9-cdb54ac69812" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: LABEL="HP_RECOVERY" UUID="2012FB0812FAE1A8" TYPE="ntfs" 
/dev/sda3: LABEL="OS_TOOLS" UUID="9CCC8FE8CC8FBB52" TYPE="ntfs" 
/dev/sda5: UUID="57901173-89fe-4159-9be7-88afbeaf813f" TYPE="ext3" 
/dev/sda6: UUID="fa1bcea3-f0ff-42bd-a238-481b4f909bd5" TYPE="swap" 
ubuntu@ubuntu:~$

---

### Post by roelforg on 2012-04-08
```

sudo fsck /dev/disk/by-uuid/57901173-89fe-4159-9be7-88afbeaf813f

```
can't hurt to check the fs.

---

### Post by latestarter on 2012-04-08
ubuntu@ubuntu:~$ sudo fsck /dev/disk/by-uuid/57901173-89fe-4159-9be7-88afbeaf813f
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda5: recovering journal
Error reading block 17393 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>?

---

### Post by roelforg on 2012-04-08
You can have fsck fix it for you:
```

sudo e2fsck -p /dev/disk/by-uuid/57901173-89fe-4159-9be7-88afbeaf813f

```

Man page: [http://manpages.ubuntu.com/manpages/oneiric/man8/e2fsck.static.8.html](http://manpages.ubuntu.com/manpages/oneiric/man8/e2fsck.static.8.html)

---

### Post by latestarter on 2012-04-08
ubuntu@ubuntu:~$ sudo e2fsck -p /dev/disk/by-uuid/57901173-89fe-4159-9be7-88afbeaf813f
/dev/disk/by-uuid/57901173-89fe-4159-9be7-88afbeaf813f: clean, 629489/6406144 files, 10803930/25599569 blocks
ubuntu@ubuntu:~$

---

### Post by roelforg on 2012-04-08
Does it boot now?

---

### Post by latestarter on 2012-04-08
Still no 'grub' and still defaulting to Vista on boot up.

---

### Post by roelforg on 2012-04-08
> **latestarter said:**
> Still no 'grub' and still defaulting to Vista on boot up.

Is it wubi?
if not
Does it have a dedicated drive for ubuntu?
if not, run update-grub (might break vista's bootloader, but that's easy to fix from grub, but i still don 't garantee success)

---

### Post by latestarter on 2012-04-08
Just one drive for both.
update-grub results
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

---

### Post by roelforg on 2012-04-10
> **latestarter said:**
> Just one drive for both.
update-grub results
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

Try boot-repair [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
It should be in the repo's, i think...

---

