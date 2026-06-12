---
title: "Mediatomb? Files on FAt32 drive?"
date: 2009-08-12
forum: General Help
---

### Post by esc0bar on 2009-08-12
Hello,

As I said in my last post, I modified my partitions to include a FAT32 partition to share my music and videos between ubuntu and win7. I installed Mediatomb but I can't seem to find a way to share files on my FAT32 parittion. It seems to only look at the Ubuntu partition...

It's for streaming to my PS3. Anyone knows a solution for mediatomb to share files form my FAT32 drives to the ps3? On Win7 I use Tversity and everything is fine. Is there another program I could use on Ubuntu?

Thanks

---

### Post by rajeev1204 on 2009-08-12
Could you give more details please.

---

### Post by t0p on 2009-08-12
I don't know if this will fix your mediatomb problem, but I advise you to reformat your shared partition as NTFS.  I think FAT32 is a pretty crummy file system format, and as Ubuntu uses NTFS just fine, it's the way to go.

---

### Post by Mi*6d@# on 2009-08-12
Well, he could reformat the partition to ext4 and then install the driver for Win7...

---

### Post by mcduck on 2009-08-12
> **esc0bar said:**
> Hello,

As I said in my last post, I modified my partitions to include a FAT32 partition to share my music and videos between ubuntu and win7. I installed Mediatomb but I can't seem to find a way to share files on my FAT32 parittion. It seems to only look at the Ubuntu partition...

It's for streaming to my PS3. Anyone knows a solution for mediatomb to share files form my FAT32 drives to the ps3? On Win7 I use Tversity and everything is fine. Is there another program I could use on Ubuntu?

Thanks

How (and where) is your FAT partition mounted? If the drive is now automatically mounted try mounting it permanently with /etc/fstab instead.

---

