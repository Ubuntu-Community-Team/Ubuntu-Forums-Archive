---
title: "iPod Trouble"
date: 2009-10-18
forum: General Help
---

### Post by smithpercussion on 2009-10-18
I'm afraid I've gotten myself in quite a pickle.

I have a linux formatted Ipod (Generation 5 80gb Video Ipod)

I formatted it because Ubuntu was not able to mount my ipod before.. Unfortunately it still can't.

I am trying to install rockbox but first it seems that I need to mount the device. Right now it is formatted to ext2.

Thank you in advance for your assistance!

---

### Post by smithpercussion on 2009-10-18
```
sudo mount /dev/sr0 /media/usb


mount: block device /dev/sr0 is write-protected, mounting read-only
```

This is where I'm at.

---

### Post by Chronon on 2009-10-18
Your player needs to have an MBR and a blank partition containing the firmware along with a data partition formatted to FAT32 if you want Rockbox on it.  Ubuntu can mount a FAT32 UMS device just fine, so formatting to a different file system is not necessary.  You might need to kill gvfsd-gphoto2 (IIRC) to get your device to mount properly.

The easiest way to get your iPod into the correct state is to Restore it on a Windows installation of iTunes.  If you don't have easy access then you can find instructions on manually restoring the iPod in Rockbox's wiki.

---

### Post by smithpercussion on 2009-10-20
I appreciate your help. And although it makes sense, I am not able to access my ipod at all. A also can't access it with partition editor because once it notices my devices it force closes.

---

### Post by smithpercussion on 2009-10-20
Here some code output that may help. Let me know if you need something specific.


```


 sudo fdisk -l


Disk /dev/sdq: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdq1               1         608    19535008   83  Linux

```

and.............

```
 sudo dosfsck -a /dev/sdq


dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
Too many clusters (4883696) for FAT16 filesystem.

```

---

