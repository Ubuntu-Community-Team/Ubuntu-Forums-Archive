---
title: "Grub error 15 file not found!"
date: 2010-03-12
forum: General Help
---

### Post by Shadow12313 on 2010-03-12
After trying to boot into ubuntu grub gave me an error 15 saying the the file could not be found.

Any ideas?
Thank-you in advance.

---

### Post by spiderbatdad on 2010-03-12
I had this error once perhaps due to installing a grub loader post OS installation. You should be able to boot from a live cd and run fdisk -l.
Determine where the boot directory is and then edit the menu.lst to point the kernels to the right partition...
Looking at the grub2 files, I dont see how this is done. So I would try to mount the file system containing linux and boot flag then run update-grub...if using grub2.
Sorry not of more help. Grub2 is still a little confusing to me.
If this is as clear as mud, please say so. Someone else is likely to have a clearer solution.

---

### Post by audiomick on 2010-03-12
From here
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
> **File Not Found (Error 15)**

 This error is the result of a GRUB 2 installation to /boot but a Master Boot Record ( MBR ) which still contains Grub legacy. This can happen if you don't select your drive when running **sudo update-from-grub-legacy**. Shortly after starting this command the user will be asked to select the device (*sda, sdb, etc*). Highlight the drive and press the space bar to select it when presented with this screen. *Failure to select a drive* will result in an *Error 15*. 
To recover from this error, GRUB 2 must be reinstalled. Go to _[COLOR=Red][Reinstalling from the LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")[/COLOR]_ for instructions. 

---

### Post by spiderbatdad on 2010-03-12
> **audiomick said:**
> From here
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Ah great solution. To keep grub2 but use grub-legacy rename /etc/default/grub to /grub.old then edit /boot/grub/menu.lst at the root section of each kernel to match each partition in fdisk such as root (hd0,5)

---

