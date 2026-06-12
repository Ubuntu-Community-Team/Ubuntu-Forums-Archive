---
title: "Just finished extending partition. Now I can't boot"
date: 2010-07-24
forum: General Help
---

### Post by altjx on 2010-07-24
I just used GParted live Boot CD to extend my partition. Prior to that, I was dual booting with Windows 7. I deleted Windows 7 Partition and it turned into unallocated space. So I booted up to GParted Live Boot CD and turned Swapoff for the Linux-swap partition, and resized the extended partition to fill up the unallocated space Windows 7 had. Now after an hour of resizing the partition, I can't boot. I get the flashing white cursor in the top left. Anyone have any idea?

---

### Post by altjx on 2010-07-24
Is there a way to repair GRUB or something? Not sure why I wouldn't be able to boot just after that...

---

### Post by lindsay7 on 2010-07-24
Read up on the info on the web and this site regarding "Testdisk".  It may be able to help you.

---

### Post by oldfred on 2010-07-25
Because you did major partition changes partition number & UUIDs may have changed. Both grub and fstab need to be updated/reviewed.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
 
Reinstall grub or grub2 which ever you have (do not mix them or else you will have bigger issues). And review /etc/fstab in your install and compare all UUIDs or sdaX references with 

```
sudo blkid
```

---

