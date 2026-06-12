---
title: "convert my wubi ext3 file system to ext4"
date: 2009-10-12
forum: General Help
---

### Post by steve51184 on 2009-10-12
hey all is there a way i can convert my wubi (9.10 beta) ext3 file system to ext4?

thanks :guitar:

---

### Post by Tim Sharitt on 2009-10-13
To the best of my knowledge, the method described at [http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4](http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4) should work, but with a bit of extra work.

First, I would suggest backing up wubi's disk image (should be as simple as making a copy of C:/ubuntu/disks/root.disk from windows).

Since it's probably not a good idea to do this to a mounted file system (if it's even possible), You will need to boot a LiveCD.

After the live cd boots up, open a terminal and mount the ntfs partition where your wubi install resides.
```

sudo mkdir /win

sudo mount /dev/sda1 -t ntfs-3g /mnt/win
```
(changing sda1 to whatever device it is on your machine)

Next you need to associate the wubi image with a loop device. From what I can gather, the wubi root image is a single partition so you shouldn't need to worry about offsets.
```

losetup /dev/loop0 /win/ubuntu/disks/root.disk

```

From here, the procedure is the same as a physical disk, using /dev/loop0 as the device change.

```

tune2fs -O extents,uninit_bg,dir_index /dev/loop0

e2fsck -fpDC0 /dev/loop0

```

As it says in on the page linked above, new files will be created in extents format but old files will not be converted to use extents.

---

### Post by steve51184 on 2009-10-13
wow thank you very much

i do have one question about "extents" what is it and is it important as i won't have it for old files only new ones.. will this affect performance?

---

### Post by Tim Sharitt on 2009-10-20
An extent is a logically contiguous set of blocks within a file as well as the underlying block device. Most modern file systems put a lot of focus on assigning contiguous blocks to files as a way to increase I/O speeds, several of them using extents (in some for or other) to accomplish this. 

Ext4 uses extents to store files instead of the old block-mapping used in ext2/ext3. Not only does this reduce fragmentation, but it also cuts down on the overhead in a files meta data by replacing several block pointers with a single extent which leads to better I/O performance as well. 

As far as old files not being in extents format, I wouldn't worry about it too much. Although some people do claim see a performance difference on normal desktop systems, especially at boot, it's not a huge boost. You probably won't see a faster boot time since most of those files are the old ones, but I never could tell a difference anyway.

To be honest, since you are using a disk image residing on an ntfs drive, you may not see any difference at all.

---

### Post by P4man on 2009-10-20
> **Tim Sharitt said:**
> 

To be honest, since you are using a disk image residing on an ntfs drive, you may not see any difference at all.

+1

If the OP wants to migrate to Ext4 for performance reasons, then doing a normal install on a dedicated partition rather than a wubi install is probably a better idea (and not just for performance reasons)

---

### Post by steve51184 on 2009-10-20
> **P4man said:**
> +1

If the OP wants to migrate to Ext4 for performance reasons, then doing a normal install on a dedicated partition rather than a wubi install is probably a better idea (and not just for performance reasons)

i'd love to do this but how do i convert a wubi install to a normal install?

---

### Post by P4man on 2009-10-20
> **steve51184 said:**
> i'd love to do this but how do i convert a wubi install to a normal install?

If you must:
[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

Its fairly dated but I think it should still work. Frankly though, consider doing a fresh install. Since you're on Karmic it can not be a very old install.

edit: better link
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

---

### Post by steve51184 on 2009-10-20
it was 8.10 (maybe even 8.04) updated to 9.10 beta so it's quite old

p.s. thanks for the links

---

