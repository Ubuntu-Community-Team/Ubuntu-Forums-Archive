---
title: "Missing operating system"
date: 2011-03-05
forum: General Help
---

### Post by Kranix on 2011-03-05
Whenever I boot my laptop, after the screen you can get to the BIOS from and such, it displays this on the screen:

```
Missing operating system
```

---

### Post by Hedgehog1 on 2011-03-05
Kranix,

We need to get a look at your disk partition layout.

Please boot from the liveCD, select the 'Try' option, then:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

---

### Post by Kranix on 2011-03-05
> **Hedgehog1 said:**
> Kranix,

We need to get a look at your disk partition layout.

Please boot from the liveCD, select the 'Try' option, then:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004da1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37384   300281856   83  Linux
/dev/sda2           37384       38914    12286977    5  Extended
/dev/sda5           37384       38914    12286976   82  Linux swap / Solaris

Disk /dev/sdb: 3985 MB, 3985637376 bytes
128 heads, 42 sectors/track, 1448 cylinders
Units = cylinders of 5376 * 512 = 2752512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00014378

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1448     3892208    c  W95 FAT32 (LBA)
```

---

### Post by kiyop on 2011-03-05
In BIOS settings, which drive is the first in BOOT ORDER?

Maybe the MBRs of the HDDs do not have any boot loader.

Did you installed Ubuntu on /dev/sda1?

You can install boot loader by booting with Ubuntu Live CD.

Open the terminal and type:
```
sudo mount -t auto /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt /bin/bash
```

The prompt will be changed to
root@hogehoge:/#
Then, type
```
grub-install /dev/sda
udpate-grub
exit
```

The prompt will be back to
ubuntu@hogehoge:~$
Then, type
```
sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /mnt/dev
exit
```

Restart and remove LiveCD.

If the problem is not solved, you can use BOOT INFO SCRIPT.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Mark Phelps on 2011-03-05
Is the 4GB drive a USB thumb drive?  If so, I'm guessing that the PC is trying to boot from that.

Unless you need that drive present at boot, simply remove it, boot from the internal drive, and insert the USB drive after you're up and running.

---

