---
title: "Acidentally overwrote windows with an ext2 fs"
date: 2009-10-25
forum: General Help
---

### Post by M4rotku on 2009-10-25
Hey guys,

I was in the process of installing gentoo to a flash drive using a sysresccd and when I was creating the fs for the /boot partition, I accidentally typed '/dev/sda1' instead of '/dev/sdb1.'  Well, it worked because my windows partition (sda1) no longer boots.  While this is not a horrible loss since I haven't booted into it for a long time, it would still be nice to get it back in case I ever need it.  Is there a way to erase a layer of filesystems and go back to the old one?

Much thanks,
M4rotku

---

### Post by DeMus on 2009-10-25
> **M4rotku said:**
> Hey guys,

I was in the process of installing gentoo to a flash drive using a sysresccd and when I was creating the fs for the /boot partition, I accidentally typed '/dev/sda1' instead of '/dev/sdb1.'  Well, it worked because my windows partition (sda1) no longer boots.  While this is not a horrible loss since I haven't booted into it for a long time, it would still be nice to get it back in case I ever need it.  Is there a way to erase a layer of filesystems and go back to the old one?

Much thanks,
M4rotku

By creating the new filesystem did you also format the partition? IF so, Windows is gone, if not you could gparted to change the partition to ntfs (or fat32) again.

---

### Post by niteshifter on 2009-10-25
Hi,

If what was in front of /dev/sda1 was mkfs or mkfs.ext2 then data (id table, superblocks and such) was written to the partition - Windows is broken. As you noticed, it won't boot.

There's no such thing as "layers of file system" - there's the surface of the disk. Just one. You've changed it.

Is it recoverable? More or less, yes via testdisk. Some files won't be recoverable. Which ones? You find out by trial and error. Emphasis on the error part ;)

---

### Post by nikhilbhardwaj on 2009-10-25
hard luck
you'll have atough time recovering anything useful

happened to me once

hopefully nothing too valuable was there on that partition

---

### Post by M4rotku on 2009-10-25
Nothing important was lost.  I hadn't booted into windows in forever.  I was just wondering how it would've been done.

---

