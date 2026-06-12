---
title: "Can no longer boot XP without SD card"
date: 2010-05-08
forum: General Help
---

### Post by gdhadden on 2010-05-08
I have a EEE PC running Windows XP on the hard drive and just installed Ubuntu 10.04 on a16gb SD card. I can boot into either system when the SD card is installed, but if i remove it and try to boot, I get the prompt "grub rescue>". I can't figure out how to get to XP from this prompt. Can anyone help?
 
Thanks a lot!
 
-geo

---

### Post by ambdeep on 2010-05-08
you probably overwrote the windows boot manager with grub....go to a windows forum and check how to reinstall it....to boot into ubuntu...just install grub to your sd card and change the boot options in your bios to boot from it....

---

### Post by lmarmisa on 2010-05-08
You have installed Ubuntu in your SD card, but you have modified the code area of the loader of MBR of the hard drive (/dev/sda).

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

You can restore the loader of the XP system easily. Start the Ubuntu system (with the SD card installed), open a terminal and type:

> 
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
You should install the grub loader in the SD card now (I will suppose that your SD is the device /dev/sdb).

Please, verify if the device assigned to your SD card is /dev/sdb typing this command:

> 
sudo fdisk -l
After this verification, type the command:

> 
sudo grub-install /dev/sdb
 Change sdb to sdc, sdd, etc if neccesary according to the result of the fdsik command..

The system is fixed now. Simply restart.

Probably you will need to change the configuration of the BIOS in order to select your SD as the most prioritary device during the boot process.

Best regards,

Luis

---

### Post by gdhadden on 2010-05-08
Luis, you rock!  Thank you for the quick response.  The problem seems to be totally fixed now.

Cheers,

-geo

---

### Post by lmarmisa on 2010-05-08
Hi geo,

That sounds great.

Please, mark the thread as solved using the  Thread Tools menu at the top of the thread.

Cheers,

Luis ):P

---

