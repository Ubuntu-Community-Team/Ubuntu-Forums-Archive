---
title: "Can't mount USB stick as writable"
date: 2009-11-26
forum: General Help
---

### Post by Hawk__0 on 2009-11-26
I was using this stick not more than 5 minutes ago and copying files to and fro it.  All of a sudden it mounts with a weird name and I cannot gain write access to it!

```
There was an error copying the file into /media/e257080f-0989-4f9a-a9ba-d425194a54e0.
```
```
Error opening file '/media/e257080f-0989-4f9a-a9ba-d425194a54e0/wallpaper.jpg': Permission denied
```

---

### Post by Hawk__0 on 2009-11-27
bump...

---

### Post by Grenage on 2009-11-27
If you re-mount, does it allow write access for a further period of time?

---

### Post by Hawk__0 on 2009-11-27
No, it doesn't

---

### Post by coffeecat on 2009-11-27
As it's a USB stick I guess it's formatted FAT32. Am I correct?

And you say "weird name". Do you mean "e257080f-0989-4f9a-a9ba-d425194a54e0". That looks like a UUID to me. Were you getting a partition label before?

We need more information.

---

### Post by slumbergod on 2009-11-27
I always had issues when a Windows friend would give me USB flash drive to transfer files to after they had UNsafely removed it from Windows. I had to mount it manually to overcome the restriction on not being able to write to it. 

Here are my notes from the last time I had to mount one...maybe they can help

FORCE MOUNT CRAPPY VISTA FLASH DRIVE
make sure ntfs-config, ntfs-3g are installed...and you have a mount point already made
sudo mount -t ntfs-3g /dev/sdb1 /media/ext-USB-HDD -o force

---

### Post by Hawk__0 on 2009-11-27
These are EXT2 formatted.  They contain a thin client image on them.  I was able to write to them before... but not now...

---

### Post by coffeecat on 2009-11-27
Have you tried a fsck on it?

---

