---
title: "File copy cause system crash"
date: 2010-12-23
forum: General Help
---

### Post by SpinningAround on 2010-12-23
I have tried numerous times to transfer files from my external harddrive to my laptop, using usb-interface. Weird part is that it only occur when I try to transfer large amount of file (~7GB). What happens is that the computer lockup completely and I'm forced to make a hard reset. 

I thought that it might had something to do with GUI, so I pressed ctrl+alt+f2 and tried with 'cp' command, but the problem persisted.

I also got Windows 7 installed on the same laptop and there I can copy files without any problems, other that it seem to take a lot more time.

---

### Post by sikander3786 on 2010-12-23
Most likely, your USB drive is formatted FAT32 and FAT32 doesn't like/support files bigger than 4 GB. (4 GB if I remember??)

Try formatting your USB to NTFS (if using between Windows & Ubuntu) or Ext4 (if using between 2 Ubuntu PCs) and see if things improve.

---

### Post by SpinningAround on 2010-12-23
> **sikander3786 said:**
> Most likely, your USB drive is formatted FAT32 and FAT32 doesn't like/support files bigger than 4 GB. (4 GB if I remember??)

Try formatting your USB to NTFS (if using between Windows & Ubuntu) or Ext4 (if using between 2 Ubuntu PCs) and see if things improve.
It's NTFS and I think that ubuntu was using ntfs-3g to control the drive, atlest that what I found when I was looking in the logs. Apart for that did I not find anything strange, maybe I wasn't looking in the right log.

---

