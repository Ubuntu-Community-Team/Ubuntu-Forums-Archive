---
title: "Hibernate after partimage restore"
date: 2009-07-01
forum: General Help
---

### Post by pubear on 2009-07-01
I have a strange issue.  I have half a dozen MSI Wind netbooks that I am using for webmail and a time tracking application.  I have set them up with UNR and locked them down.  When I have done a install from scratch, hibernate works great.  I have taken a partimage image of the root partition and the home partition.  When I do a restore, everything works fine as far as I can tell, EXCEPT hibernate.

When I hibernate a manually setup netbook, I get all sorts of log goodness and a successful resume from hibernate.

On a netbook that has been restored from the partimage image, I don't get any logging whatsoever of the machine even attempting to go into hibernate, although I do see the blinking cursor for a bit as well as the HDD activity light which leads me to believe it is writing the hibernation file to swap.  However when I power it back on, the machines go straight to the normal boot process.

I am reasonably comfortable with Ubuntu and various Linuxes, but I have absolutely no idea what is going on here.  The only thing I see is an early kernel message during boot about not finding a map file in /boot/System.map-2.6.28-13-generic, but the machine that DOES hibernate has the same message.

This same issue happens whether the image is restored to the same physical netbook, to one of the other identical models, or to a slightly different model of MSI Wind.

Any ideas, or pointers where to look next?  Hibernate isn't a critical issue, but it sure would be nice.  Plus it is worrisome that my partition restore isn't 100% identical to a fresh install.

---

### Post by pubear on 2009-07-02
I finally figured this out.  It turns out that my only issue was that the /etc/initramfs-tools/conf.d/resume file was looking for the swap partition by UUID.  I had changed the fstab to use the device name instead of UUID, but didn't know about the existence of this file.  Changing this file to say "RESUME=/dev/<swappartition>", plus a rebuild of the initramfs image (sudo update-initramfs -u) fixed the issue.

---

