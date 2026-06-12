---
title: "Ubuntu 10.4 and ntfs-config issues"
date: 2010-05-04
forum: General Help
---

### Post by ProDigit on 2010-05-04
After installing Ubuntu 10.4, my 2x external USB NTFS harddrives worked perfectly fine out of the box.
In Ubuntu 9 I had some issues with those drives, namely that some files would be erased (perhaps overwritten) on the drive (as I shared the drive with bot XP, vista and Xubuntu 9). But so far Ubuntu 10 seemed to do a good job in NOT deleting the files anymore...
Nevertheless I installed ntfs-config to see what it could do (enable write support for these drives; despite that I already can write on them).
This seemed to have messed up my ubuntu a bit.

Now the system will halt upon booting, until both drives are connected (both drives are external HD's connected via USB cable).

Upon boot splash screen of Studiobuntu (which is another issue by itself I can not seem to get rid of) it gives me the option to press 's' for skipping, or 'm' for manual recovery.
I usually press 's' (it's not really nice that a user input is required to continue booting).
If I connect no drives (and press 's' twice, once for each drive), Ubuntu continues to boot and operate fine, but does not allow me to mount these 2 drives in particular. Any other drives not configured by ntfs-config will be mounted just fine.
Upon inserting the drive in the USB port after boot, Ubuntu tells me some error in a window, and that I need to be a root to mount the drive.

Here's the error message shown in ubuntu GUI:
**Unable to mount Harddrive 1**```
Error mounting: mount exited with exit code 1:helper failed 
with:
mount:only root can mount /dev/sdc1 on /media/Harddrive 1
```

I started nautilus in root (admin mode), but I still can't see the contents of the drive (In root nautilus allows me to open the drive's content, and it tells me correctly how much free space is on the drive, but it also  does not show the drive's content, no folders visible).

The only way I can see the contents of the drive, is to plug them in after grub, and before boot (because Grub sometimes complains when I leave them in from before boot).
Once the drives work fine like this in Ubuntu, and they are unplugged or unmounted, the drives no longer will mount, and a reboot is necessary.
I've tried to reset and play around with NTFS-config settings, but nothing resulted in me being able to restore my system to the way it worked before (to a normal Ubuntu).

I don't know much about Linux, but is there an easy way to fix this?

---

### Post by sisco311 on 2010-05-04
You have to remove the fstab entries created by ntfs-config.

Open a terminal and post the output of:
```
sudo blkid
```
and
```
cat /etc/fstab
```

---

### Post by ProDigit on 2010-05-13
I removed the external drives from fstab, while at the same time I enabled networking (was for some reason disabled as I booted Ubuntu), and now the drives work normally!

---

