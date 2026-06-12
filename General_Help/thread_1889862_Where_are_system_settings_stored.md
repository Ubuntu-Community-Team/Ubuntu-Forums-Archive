---
title: "Where are system settings stored?"
date: 2011-12-02
forum: General Help
---

### Post by uhuru53 on 2011-12-02
I created a UBUNTU 11.10 bootable persistent USB on a 8GB pendrive.

After a while my settings are no more saved, I cannot change the desktop or the clock settings anymore.

So I suppose that system settings should be saved somewhere in some file.

Where are system settings stored?

I've read that could be in /etc/X11/xorg.conf 

but I don't have/find that file.

So, please, where are system settings stored?
How could I change system settings?

Many thanks.

---

### Post by C.S.Cameron on 2011-12-02
In a persistent install, persistence is stored in a file named casper-rw.
Max size is 4GB if the pendrive is formatted FAT32, (2GB if FAT).
If you need more space you can make a ext4 partition and name it casper-rw or home-rw.
You can mount the casper-rw file to access it's contents:

```

mount -o loop casper-rw-1000M /mnt/odd2fs/
```

---

