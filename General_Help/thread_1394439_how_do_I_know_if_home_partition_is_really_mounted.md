---
title: "how do I know if /home partition is really mounted"
date: 2010-01-30
forum: General Help
---

### Post by scottac on 2010-01-30
Alright. So I am running ubuntu 9.10. My disk is partitioned as follows

/dev/sdb1 4 GB swab 
/dev/sdb2 15 GB ext3 root

and then I had an unused 55 GB partition that I decided I wanted to use as my home directory so I added the following line to the bottom of /etc/fstab

```
/dev/sdb3	/home/fredo	ext3 	defaults,umask=0 0 0
```

Note /dev/sdb3 is the 55 GB ext3 partition previously mentioned.

I then rebooted.

I opened up Gparted to see if the disk had mounted (I don't know another way to check this) and sure enough /dev/sdb3 shows up with a mount point of /home/fredo

Now here is why I am a little confused.  I haven't copied anything to this partition yet and I was assuming that there would be no files on this partition but all the files that were on my previous /home directory seem to still be there without me having to copy them over.

Were these files just copied over automatically? Is this disk properly mounted as my home directory?

Thoroughly confused... please help...

---

### Post by Leppie on 2010-01-30
you can check it like this:
```
df -h
```but i'm sure it's not mounted.
you're fstab entry should be something like this:
```
/dev/sdb3    /home/fredo    ext3     defaults,relatime 0 2
```

---

### Post by dcstar on 2010-01-30
> **scottac said:**
> 
.......
I opened up Gparted to see if the disk had mounted (**I don't know another way to check this**) and sure enough /dev/sdb3 shows up with a mount point of /home/fredo
.......

```
mount | grep home
```

---

