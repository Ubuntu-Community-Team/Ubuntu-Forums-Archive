---
title: "Ubuntu USB boot issues"
date: 2012-02-15
forum: General Help
---

### Post by CaptinGoogle on 2012-02-15
I installed Ubuntu 10.10 onto a USB drive so I could carry it around instead of my laptop. 

I got Ubuntu it to install on the USB without issue but whenever I try and boot from the USB it does nothing but flash a little line in the upper-left-hand corner. I followed [https://wiki.ubuntu.com/LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") but the file menu.lst does not exist in /boot/grub.

Any help would be appreciated.

---

### Post by Leppie on 2012-02-15
ubuntu 10.10 uses grub 2, which does not use the menu.lst file but grub.cfg.

does your machine support booting off usb drives?

---

### Post by CaptinGoogle on 2012-02-15
> **Leppie said:**
> ubuntu 10.10 uses grub 2, which does not use the menu.lst file but grub.cfg.

does your machine support booting off usb drives?

Yes it does support booting off USB drives. Is there a way I can alter grub.cfg in a similar way that was suggested in the link I previously provided?

---

### Post by Leppie on 2012-02-15
> **CaptinGoogle said:**
> Is there a way I can alter grub.cfg in a similar way that was suggested in the link I previously provided?
the file is located in the folder /boot/grub
the preferred way of updating the file would be using update-grub though. howver, since you cannot boot off the usb stick at the moment the alternative would be a chroot.

---

### Post by CaptinGoogle on 2012-02-15
> **Leppie said:**
> the file is located in the folder /boot/grub
the preferred way of updating the file would be using update-grub though. howver, since you cannot boot off the usb stick at the moment the alternative would be a chroot.

Could you help provide me with some commands? I don't know enough about chroot to not mess things up further.

---

### Post by Leppie on 2012-02-15
The easier thing to do would be modifying the grub.cfg file, assuming you know what you need to put in there.
Chrooting would be the alternative, e.g. try that if the previous fails.

---

