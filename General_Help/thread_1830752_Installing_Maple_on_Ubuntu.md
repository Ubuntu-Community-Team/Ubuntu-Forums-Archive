---
title: "Installing Maple on Ubuntu"
date: 2011-08-22
forum: General Help
---

### Post by Xander314 on 2011-08-22
Sorry if this is the wrong section - I wasn't sure where to put it really.

I want to install Maple on Ubuntu, but whenever I put in one of my Maple CDs (Maple 11 or 13), it doesn't appear on the desktop, or in the /media/ folder.

On the other hand, I have tried a few non Maple CDs, all of which mount successfully. Any ideas as to why the Maple CDs won't, and/or what I can do about it?

Thanks,
Xander

PS: One of the Maple 11 CDs is specifically labelled as for Linux installation, and it doesn't mount either.

---

### Post by sanderd17 on 2011-08-22
can you mount it manually?

```

sudo mkdir /media/mycd
sudo mount /dev/sr0 /media/mycd

```

For the case that sr0 is not your CD drive, take a look in the /dev directory and try to guess what could be your CD drive. E.g. if you have a file /dev/dvd, try

```

sudo mount /dev/dvd /media/mycd

```

and do check the contents of /media/mycd each time you mount it.

afterwards, you can unmount it with

```

sudo umount /media/mycd
sudo rm -r /media/mycd

```

---

### Post by Xander314 on 2011-08-22
Thanks. I had to additionally specify the filesystem as ISO9660, but it's now mounted the drive and hopefully I can install Maple smoothly.

Just for future readers of the thread, my final commands were:
```

sudo mkdir /media/mycd/
sudo mount -t iso9660 /dev/sr0 /media/mycd/

```

If I mount manually, do I have to unmount manually, or can I just take the disc out as normal?

---

### Post by sanderd17 on 2011-08-22
> **Xander314 said:**
> Thanks. I had to additionally specify the filesystem as ISO9660, but it's now mounted the drive and hopefully I can install Maple smoothly.

Just for future readers of the thread, my final commands were:
```

sudo mkdir /media/mycd/
sudo mount -t iso9660 /dev/sr0 /media/mycd/

```

If I mount manually, do I have to unmount manually, or can I just take the disc out as normal?

If you take out the disk, you will still have an empty directory in /media, so you need to delete that afterwards (as root).

---

### Post by Xander314 on 2011-08-22
I see. Thanks again for your help :)

---

