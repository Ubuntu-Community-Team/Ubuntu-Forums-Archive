---
title: "One or more of the mounts..."
date: 2009-12-14
forum: General Help
---

### Post by Mainlake on 2009-12-14
Hi all,

I've seen some discussion on this subject, they seem not to match my problem exactly.

Yesterday when I turned the computer of, I got a beeping sound, but no error msg to screen and the computer closed down otherwise normally.
So now I'm trying to boot in Kubuntu I get screen saying:
```
one or more of the mounts listed in /etc/fstab cannot yet be mounted:
/home: waiting for UUID=XX...f2f
press ESC for recovery shell
```

In recovery shell /etc/fstab shows that /home was on /dev/sda3.
And blkid doesn't show /dev/sda3 listed.

So what would be the next step?

---

### Post by cariboo on 2009-12-14
Do you have a separate home partition? If so where is it located? What does blkid say?

---

### Post by Mainlake on 2009-12-15
> **cariboo907 said:**
> Do you have a separate home partition? If so where is it located? What does blkid say?

Yes, the home partition is separated from /. And I assume it is located in /dev/sda3.

And here is my /etc/fstab:
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=03a6ea96-e31d-4fcb-afff-601fa6b6b9ff /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=78025acb-4e7d-40dc-a895-74faa3eae2f2 /home           ext3    relatime        0       2
# swap was on /dev/sda2 during installation
UUID=432efa5c-93d7-4c9d-8103-4ff3a7325aaa none            swap    sw              0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

I'll post blkid, as soon as a get it (in half an hour).

And here is the blkid:
```
/dev/sda1: UUID="03a6ea96-e31d-4fcb-afff-601fa6b6b9ff" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="432efa5c-93d7-4c9d-8103-4ff3a7325aaa" TYPE="swap" 
/dev/sdb1: UUID="4E7881BB7881A277" LABEL="Jimi" TYPE="ntfs" 
/dev/sdb5: UUID="DE9C50FB9C50CF9F" LABEL="Pelit" TYPE="ntfs" 
/dev/sdb6: UUID="DAA00DF6A00DDA41" LABEL="Musa" TYPE="ntfs" 
/dev/sdb7: UUID="6638D8D038D8A07B" LABEL="LisM-d" TYPE="ntfs" 
/dev/sdc1: LABEL="/boot1" UUID="8cd95c97-e9ba-4905-9db1-067186e1fd78" TYPE="ext3" 
/dev/sdc5: UUID="922869F32869D72F" LABEL="Filmit" TYPE="ntfs" 

```

---

### Post by Mainlake on 2009-12-17
Anybody got any ideas?
I haven't done anything in this issue, so any help would be appreciated.

---

### Post by Mainlake on 2009-12-17
Little update: Started the computer from an USB Kubuntu netbook edition and run fsck for /dev/sda3. It didn't find any errors.

Ok, I solved problem in some degree. I edited the /etc/fstab file, instead of:```
UUID=78025acb-4e7d-40dc-a895-74faa3eae2f2 /home           ext3    relatime        0       2

```

I used the device directly:
```
/dev/sda3 /home           ext3    relatime        0       2

```

Now I'm able to boot to Kubuntu.

But the question remains, is this the correct solution?
Or should one use UUID values instead?
And does this change affect my system in some way?

---

