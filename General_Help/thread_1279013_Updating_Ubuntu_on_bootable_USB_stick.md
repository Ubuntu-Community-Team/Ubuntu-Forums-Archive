---
title: "Updating Ubuntu on bootable USB stick"
date: 2009-09-30
forum: General Help
---

### Post by paul_h on 2009-09-30
In order to demonstrate Ubuntu on computers of MS Windows users I have installed Ubuntu 9.04 on bootable 2GB and 4GB memory sticks using USB Startup Disk Creator. However, I have been unable to fully update them successfully.

If I let Update Manager run the full 160MB (approx) of updates currently needed the system crashes when it gets almost to the end of the updates installation with an error message indicating that there is insufficient space.

It will happily handle the 80MB or so of security updates but if I tell it to do the 80MB or so of recommended updates it will not complete.

In my last attempt I broke the 163MB Update into 4 parcels ... 50MB, 30MB (security), 50MB and 33MB (recommended). The update proceeded OK for the first three Update parcels but failed to install the final parcel. "failed in buffer_write(fd)" seemed to be the main cause.

The system still worked but when an application such as OpenOffice needed to write something to storage a "...no space..." message would be given.

I appears to me that the update process is not freeing up storage space no longer required after installation of preceding Update files.

Is there a solution? Is there a bug/limitation in the update process?

Paul.

---

### Post by falconindy on 2009-09-30
Clean out your downloaded archive cache with:
```
sudo apt-get clean && sudo apt-get autoclean
```

---

### Post by Giblet5 on 2009-09-30
That, plus buy a bigger stick.

16G sticks are $35.

---

### Post by scottuss on 2009-09-30
Have you checked that you actually have enough space left?

This may seem obvious, but usually, when your computer tells you something, it's a good starting point.

You can open a terminal and type ```
df
``` to see the percentage use of all of your drives. Find your USB stick and see what percent is used.

Hope that helps :)

---

### Post by Megrimn on 2009-09-30
you could just delete everything from the sticks and then install the updated version.

---

### Post by dwinks on 2009-09-30
> **Giblet5 said:**
> That, plus buy a bigger stick.

16G sticks are $35.

**Fast**16GB sticks are quite a bit more than $35.

I'd get a 200x 8GB one for around $30.

Alternatively, you could mount a tmpfs filesystem on top of /var/cache/apt/archives just before you do apt-get update && apt-get upgrade, provided you can make a 1+ ram disk.  Or toss another 2GB+ drive in and do the same.

---

### Post by Giblet5 on 2009-09-30
> **dwinks said:**
> **Fast**16GB sticks are quite a bit more than $35.

I'd get a 200x 8GB one for around $30.

Alternatively, you could mount a tmpfs filesystem on top of /var/cache/apt/archives just before you do apt-get update && apt-get upgrade, provided you can make a 1+ ram disk.  Or toss another 2GB+ drive in and do the same.


Sam's club had 'em yesterday, $34.95 for a 16G Memorex stick.

It wasn't a sale.

Admittedly, not a fast stick, but any stick that works is better than any stick that does not.

---

### Post by h6w on 2009-10-11
Hang on guys.

The original question was about upgrading on a 2GB or 4GB stick.

An initial installation, the space taken up in rootfs is only 39M, but for some reason Ubuntu Startup Disk Creator only allocates 522M to root.  Even including the rofs partition, that's still only 734MB, leaving ~1.2GB (on 2GB stick) or ~3.2GB (on a 4GB stick) for upgrades.

I have the same problem on a 16GB USB key with 8GB allocated to ubuntu.  Still only 522MB is allocated to rootfs, so Update Manager says it doesn't have enough room on a fresh install.

I think the rootfs creation is in error.  /cdrom is allocated 16GB, even though I only requested 8GB.

So how does one expand the rootfs partition?

---

