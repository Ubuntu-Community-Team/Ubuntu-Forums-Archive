---
title: "External HDD - Access With OS X and Windows"
date: 2009-12-18
forum: General Help
---

### Post by kwanbis on 2009-12-18
I have 2 1.5TB external hdds with NTFS, as i need support for more than 4GB files.

I'm intending to finally convert to Linux, and hopefully never get back to Windows.

Now, what would be the best filesystem for those external HDDs, so i can access them with my Ubuntu, with OS X, and with Windows, if needed?

---

### Post by Bucky Ball on 2009-12-18
Ntfs

---

### Post by raymondh on 2009-12-18
> **bucky ball said:**
> ntfs

+ 1

---

### Post by kwanbis on 2009-12-19
So, is the NTFS driver good enough for read and WRITE?

(first post under 9.10 ;))

---

### Post by Bucky Ball on 2009-12-19
Perfect. You will find ntfs-3g in the repositories. It will identify and mount all and any ntfs partitions you wish. It also re-writes the fstab file so these drives/partitions will mount at boot (you'll know what I mean as you get more into Ubuntu).

---

### Post by kwanbis on 2009-12-19
Strange thing is that i'm writing to NTFS usb hdds, without installing that, could it be that it is installed by default now?

---

### Post by Bucky Ball on 2009-12-20
That may depend on the version I guess. Ubuntu will pick up ntfs 'out of the box' but it you need to write it into the fstab if you add a new one. In your case, when you switch the drive on it is auto-mounting as a USB device. For internal or external NTFS drives to mount when you switch the machine on, ntfs-3g will re-write the fstab file for you to include the ntfs drives/partitions you select to mount at boot. In a terminal:

```
sudo apt-get install ntfs-3g ntfs-config
```... if you want to play with it.

When an external drive is switched on 'on the fly' it should auto-mount, regardless of format. I have an external SATA drive in three ntfs partitions. When I switch it on there they are. I use 8.04 LTS. All this may be slightly different in more recent releases.

---

### Post by kwanbis on 2009-12-20
I'm on 9.10. All the hdds are external (usb), and they all load and i can read/write to them without issues.

I would install the drivers you mention if i find any issues.

Thanks for your help.

---

