---
title: "vfat mounts using uuid?"
date: 2010-11-16
forum: General Help
---

### Post by Cool Javelin on 2010-11-16
I moved some win98 drives into my 10.04 server, and would like to add them to my fstab file.

Do vfat partitions have uuid's?

If yes, how do I get that number?

If no, I can use /dev/sdc1, and /dev/sdd1, can I get an idea what the fstab line will look like?

Do I need to create the mount points (say, /WindowsCdrive) before the fstab will mount the partition?

Thanks for your help,
Mark.

---

### Post by sisco311 on 2010-11-16
> **Cool Javelin said:**
> I moved some win98 drives into my 10.04 server, and would like to add them to my fstab file.

Do vfat partitions have uuid's?

If yes, how do I get that number?


```
sudo blkid -c /dev/null -o list
```

> **Cool Javelin said:**
> 
If no, I can use /dev/sdc1, and /dev/sdd1, can I get an idea what the fstab line will look like?


```
UUID=**uuid-here**    /mount/point    vfat    defaults,uid=**user**,gid=**group**,dmask=002,fmask=113    0    0
```

> **Cool Javelin said:**
> 
Do I need to create the mount points (say, /WindowsCdrive) before the fstab will mount the partition?

Thanks for your help,
Mark.

Yes.

For details, check out [thread=283131]How to fstab[/thread]

---

### Post by efflandt on 2010-11-16
Probably simply: **blkid**

FAT32 has a shorter 8 digit UUID with dash in the middle, and ntfs has a shorter UUID than Linux partitions:

/dev/sda1: UUID="EED2-7775" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="E6CAD622CAD5EF35" TYPE="ntfs" 
/dev/sda3: LABEL="OS" UUID="6440DA0C40D9E538" TYPE="ntfs" 
/dev/sda4: UUID="b0236a24-e5cf-4942-9e65-0b427ca1267a" TYPE="ext4"

You first need to create a mount point, like: **sudo mkdir /media/win98c**

For /etc/fstab

actual_vfat_UUID /media/win98c vfat defaults,noexec 0 0

Or if you do not want it to auto mount, but just when you do **mount /media/win98c**, you could use options **defaults,noauto,noexec**.  The noexec is because otherwise all files on FAT32 would appear to be executable, and you probably do not want to execute arbitrary Windows files or programs from Linux.

See **man fstab** and **man mount** for other options.  Someone else may have other suggestions for fstab, since I just use "Places" to automount Windows partitions when needed, with nothing about them in fstab.

---

### Post by Cool Javelin on 2010-11-16
Thank you both

sisco311

and

efflandt

The ubuntu community is a great place to shop despite the rising taxes.

Mark.

---

