---
title: "Can't reinstall GRUB to MBR"
date: 2006-05-13
forum: General Help
---

### Post by HokeyFry on 2006-05-13
Hey...

I recently reinstalled Windows (against my will I might add), and I am having trouble reinstalling GRUB to the MBR. I had a similar problem in the past, fixed reinstalled GRUB, and wrote down the steps I took. But now it no longer works. 

I had two ways documented; one was using the 'grub' command on the live CD, and the other was using 'grub-install /dev/hda'. Neither works now. I suspect that it may be due to the fact that I had to delete the FAT partition, which was /dev/hda1 before, and now hda1 is NTFS.](*,) 

Does anyone know how I can reinstall GRUB to the master boot record under these conditions?

---

### Post by Herman on 2006-05-13
>  I suspect that it may be due to the fact that I had to delete the FAT partition, which was /dev/hda1 before, and now hda1 is NTFSThat is a popular misconception. The MBR is in the first tack of the first hard disk which is often mainly empty and it is seperate from your NTFS or FAT32 or any other filesystem. Just try the command: ```
~$ sudo fdisk -lu
``` from your live cd or Ubuntu terminal and you'll see that your first partition begins at sector 63, not at sector 1, which is your MBR.

Anyway, to solve your problem...the methods you already tried should work, maybe just try again. Perhaps check the [Ubuntu Wiki's]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28MBR%29") info on the subject and make sure your methods agree with  the methods there.
Check in you BIOS for any MBR protection or anti-virus programs that might have the MBR locked. Regards, Herman :D

---

### Post by Herman on 2006-05-13
Oops, double post, Sorry.

---

### Post by HokeyFry on 2006-05-14
hmm... it could actually be the BIOS, i recently upgraded it, so that could be the problem. ill check that, thanks.

---

