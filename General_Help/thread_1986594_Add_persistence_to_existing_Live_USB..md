---
title: "Add persistence to existing Live USB."
date: 2012-05-25
forum: General Help
---

### Post by Pagnell on 2012-05-25
I know how to create a persistent bootable USB Live Ubuntu image from scratch, but is it possible to add persistence to an existing bootable Live USB stick?

Cheers in advance.

---

### Post by wilee-nilee on 2012-05-25
> **Pagnell said:**
> I know how to create a persistent bootable USB Live Ubuntu image from scratch, but is it possible to add persistence to an existing bootable Live USB stick?

Cheers in advance.

Not sure actually, you can make a usb with a persistent then make a partition called casper-rw to get a larger persistent and remove the casper in the ISO partition. There probably is a way I don't see it with a quick google foo.

Although the multisystem multiloader will allow you to make a persistent at any time on a single ISO setup.

---

### Post by Pagnell on 2012-05-25
Thanks for the response. I only ask because I have lost my ISO and have a slow connection at work and don't want to have to download it again. Oh well, needs must! Should only take about 5 hours.

---

### Post by C.S.Cameron on 2012-05-25
Sure, 
Make a partition named casper-rw, (or make a casper-rw file).

If you used Startup disk creator to make your stick, go to  disk / syslinux / text.cfg and add "persistent" as shown below:

append  noprompt cdrom-detect/try-usb=true **persistent** file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --.

---

### Post by Strojar on 2012-05-26
i use PDL Casper-RW Creator to make a persistent file from Windows.
[http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/](http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/)

---

