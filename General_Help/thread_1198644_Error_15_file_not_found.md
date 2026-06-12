---
title: "Error 15: file not found"
date: 2009-06-27
forum: General Help
---

### Post by goldencako on 2009-06-27
I've recently reinstalled my Windows, and I'm supposed to be dual-booting it along with Ubuntu 9.04. I followed the standard instructions of, after installing Windows back, running the live-cd and running these commands:
```
grub
find /boot/grub/stage1
root (hd0,1)
setup (hd0,1)
quit
```

At first this worked, and I booted Ubuntu with no problems. However, the next time I tried to boot Ubuntu I got the Error 15: file not found error. I looked all over the forums for a solution to my problem and ended up running the same commands I used before to setup GRUB again. I had no problems and all the commands worked. However the error 15 still persisted. So I ran the live-cd one more time. This time, when I ran ```
find /boot/grub/stage1
``` it said the file was not found again. Since I read that this is only to know where I should boot from, I tried running ```
root (hd0,1)
``` to no avail. All the files exist and my menu.lst is properly configured. I don't know what else to do except reinstalling Ubuntu, which, right now, is not an option.

---

### Post by merlinus on 2009-06-27
Post results of

```

sudo fdisk -l

```

and do you want to install grub in the mbr of your hdd?

---

### Post by Locutus_of_Borg on 2009-06-27
boot from livecd, open terminal, become root, mount ubuntu install to /mnt, issue following command:```
grub-install --no-floppy --root-directory=/mnt /dev/sda
``` edit the menu.lst to ensure it is pointing to the correct drive, correct kernel, and correct initrd, reboot without cd

---

### Post by goldencako on 2009-06-28
> **merlinus said:**
> Post results of

```

sudo fdisk -l

```

and do you want to install grub in the mbr of your hdd?
Here it is:
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc257c257

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4462    35840983+   7  HPFS/NTFS
/dev/sda2            4463       11145    53681197+   b  W95 FAT32
/dev/sda3           11146       14332    25599577+  83  Linux
/dev/sda4           14333       14593     2096482+  82  Linux swap / Solaris

```


> **Locutus_of_Borg said:**
> boot from livecd, open terminal, become root, mount ubuntu install to /mnt, issue following command:```
grub-install --no-floppy --root-directory=/mnt /dev/sda
``` edit the menu.lst to ensure it is pointing to the correct drive, correct kernel, and correct initrd, reboot without cd

Following are the commands and their respective responses. The error still persists.
```
sudo grub-install --no-floppy --root-directory=/mnt/ /dev/sda

Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /mnt//boot: Not found or not a block device.
``` 
```
sudo grub-install --no-floppy --root-directory=/media/disk/mnt/ /dev/sda

Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /media/disk/mnt//boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/media/disk/mnt//boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /media/disk/mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda
```

Note that /media/disk/ is where my filesystem is mounted.

---

### Post by merlinus on 2009-06-28
Try this:

```

sudo grub 
root (hd0,2)
setup (hd0)
quit

```

---

### Post by Locutus_of_Borg on 2009-06-28
well, yeah, you have to put the actual mount point as the root-directory option

it looks like it all went okay after that, is there still a problem?

---

### Post by goldencako on 2009-06-29
> **merlinus said:**
> Try this:

```

sudo grub 
root (hd0,2)
setup (hd0)
quit

```

Ok, so I tried that, and it appeared as though everything was running smoothly. Had no error messages and it seemed as thought it was going to work. But it didn't :(
Is there any other way to solve this problem? Maybe installing GRUB somewhere else, or editing the windows boot.ini?

---

### Post by merlinus on 2009-06-29
supergrub may work.  Unfortunately the server seems to be down at the moment.

[http://supergrubdisk.org](http://supergrubdisk.org)

---

### Post by goldencako on 2009-06-29
I checked it out. At first I tried the Auto version (screen shot attached) and then I tried booting my Jaunty through the normal Super Grub. The text showed no errors, but the processes of booting simply stopped at
```
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...
```
So, no booting yet.

---

### Post by goldencako on 2009-07-09
Nothing, yet? I'm considering getting an external HD, backing everything up and starting fresh. It feels dissapointing though, since the OS itself is not broken, just GRUB.

---

