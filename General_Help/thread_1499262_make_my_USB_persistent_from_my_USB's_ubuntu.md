---
title: "make my USB persistent from my USB's ubuntu"
date: 2010-06-01
forum: General Help
---

### Post by h3llt0y0 on 2010-06-01
Hello everyone,

I have recently installed Ubuntu's latest version on my 16gb Kingston datatraveller 2.0 and I was wondering if it was possible for me to change my ubuntu settings so that my USB would be persistent from that same USB on Ubuntu? ok maybe a little confusing i'll grant it. Let's put it this way: If I were to boot my computer on my USB and log into Ubuntu, would I have the ability at that time to change that same USB to persistent mode?

Thank you to all who help in advance :)

---

### Post by C.S.Cameron on 2010-06-01
There are two methods to choose from.

Make an ext(2,3 or 4) partition on your thumbdrive and name it casper-rw.
Go to / syslinux / text.cfg and added "persistent" as shown below:

append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --

(If you are booting the pendrive while editing the file, it is found in the cdrom folder).

If you make a home-rw partition your home folder will be saved there.

Or go to pendrivelinux and get their casper-rw file kit.
and then make the above modifications to text.cfg.

---

### Post by h3llt0y0 on 2010-06-02
Thanks it worked :D

---

