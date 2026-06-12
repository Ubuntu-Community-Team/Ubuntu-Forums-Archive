---
title: "I have just wrote PC-BSD disk image on sda. How can I get back to ubuntu?"
date: 2011-10-30
forum: General Help
---

### Post by ugiulio on 2011-10-30
Hello all,

I downloaded PC-BSD disk image (I'd like to test this OS on a second pc). But I have just done a terrible error! I wrote the following command in the shell: dd if=<path>/PCBSD.img of=/dev/sda thinking that this command had written the disk image on the USB stick... I have followed the PCBSD wiki [http://wiki.pcbsd.org/index.php/Burning_the_Installation_Media](http://wiki.pcbsd.org/index.php/Burning_the_Installation_Media) In particular this note says: On Linux, use "/dev/sda" to refer to the first USB device (instead of of=/dev/da0).

So right  now I get an empty USB stick and BSD luncher after I reboot my pc. How can I get back to my ubuntu OS? I have just checked that all my files are still in the hard drive, but I am not able to load ubuntu. Can someone help me, please?

Regards,
Giulio.

PS My set up is: one single hard drive with no dualboot; plain ubuntu 11.10

PPS Sorry for the error in the title: I have just written ......

---

### Post by The Cog on 2011-10-30
That wiki is (as you have discovered) shockingly wrong. sda is generally the first hard drive, not the first usb drive. I wonder how many other people have also had their PCs trashed by that bad wiki entry.

I am surprised to hear that you can still see all your files on the hard drive. How did you manage to see them? Back them up to a USB hard disk now, if you can.

I would have thought that your hard disk partition table is now wrong, overwritten with the one from the image file. I believe that there are live CDs that can attempt to guess what the partition table looked like and replace it, but I don't even know there names. If it were me, I would simply reinstall from scratch, but it may be worth waiting to see if someone else has any better ideas.

---

### Post by ugiulio on 2011-10-30
First of all thank you for you reply.

1) I didn't know what really happened. I can tell you that after I have done the dd command ubuntu was still working. Then I shut down my pc. At the following session I saw the BSD launcher instead of Ubuntu.

2) I haven't personally checked that all my files are still in the hard drive. I gave it to my friend. And he showed me all that..... but he is not able to recover the Ubuntu OS without erasing all data. He can only save all my files onto an USB drive.

I will wait for a different way till late Monday. Then I will be forced to follow your advice.

PS: What would have been the right command to write the BSD image onto the first USB external drive?

---

### Post by The Cog on 2011-10-30
> PS: What would have been the right command to write the BSD image onto the first USB external drive?That's not set in stone. On my PC, I've seen them appear as sdb, sde, sdf in the past. The command ```
sudo fdisk -l
``` will list the hard disks present. You can work out from their sizes which is which, or try the command before and after plugging the usb drive in to see which is the new one.

---

