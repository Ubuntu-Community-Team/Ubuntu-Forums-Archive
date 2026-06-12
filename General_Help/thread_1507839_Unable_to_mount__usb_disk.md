---
title: "Unable to mount  usb disk"
date: 2010-06-12
forum: General Help
---

### Post by YigalB on 2010-06-12
I am trying to copy content from my Ubuntu computer into XP computer by using external USB disk (250GB Samsung). 
(I have to do it that way because once I installed Lucid, I lost the ability to connect the Ubuntu to the home networking).

Now I get the "Unable to mount SMNG usb", with:
> Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.



Any idea why?

---

### Post by pastalavista on 2010-06-12
Just a guess but I'd say "NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware". Probably would have been better to have formatted the drive as FAT32 because it doesn't have all the NTFS security "tweaks". Remount it in Windows and run checkdisk and "safely remove" it and it might work.

Also, you need to install Samba to network with Windows computers.

---

### Post by YigalB on 2010-06-12
> **pastalavista said:**
> Just a guess but I'd say "NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware". Probably would have been better to have formatted the drive as FAT32 because it doesn't have all the NTFS security "tweaks". Remount it in Windows and run checkdisk and "safely remove" it and it might work. But I don't understand... it won't mount on Ubuntu? isn't that where the data came from?

the data currently on disk was written from Windows. I just wanted to use the empty space to copy from Ubuntu.


[/QUOTE]
Also, you need to install Samba to network with Windows computers.[/QUOTE]
I did - although with previous versions of Ubuntu I didn't have to do anything - it always recognized the home network automatically. I have no idea why things are different with Lucid.

---

### Post by efflandt on 2010-06-12
At some point did you disconnect the drive without "safely removing" the USB drive from a computer?  Did you maybe put a disk volume on it instead of a regular ntfs partition?  What does **sudo fdisk -l** (small L) show for the drive?

Have you tried running **chkdsk /f** on the drive from Windows DOS like command window on another computer to see if that fixes it?

The only time I had trouble reading ntfs on (laptop) USB drives in external enclosure was when the filesystem or disk was corrupted.  And except in the case when the disk was totally failing, **chkdsk /f** from Windows fixed that (even when a disk had some bad sectors).

---

### Post by YigalB on 2010-06-12
> **efflandt said:**
> At some point did you disconnect the drive without "safely removing" the USB drive from a computer?  Did you maybe put a disk volume on it instead of a regular ntfs partition?  What does **sudo fdisk -l** (small L) show for the drive?

Have you tried running **chkdsk /f** on the drive from Windows DOS like command window on another computer to see if that fixes it?

The only time I had trouble reading ntfs on (laptop) USB drives in external enclosure was when the filesystem or disk was corrupted.  And except in the case when the disk was totally failing, **chkdsk /f** from Windows fixed that (even when a disk had some bad sectors).

I don't recall removing without "safe".
I didn't run chkdsk on windows yet

> 
Disk /dev/sdb: 160.0 GB, 160041885184 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb4249474



---

