---
title: "ubuntu on usb and windows on hd, how and where to set grubto set grub"
date: 2009-10-02
forum: General Help
---

### Post by chriskin on 2009-10-02
a friend got ubuntu on a usb flash drive and windows on the primary hd
how should we set grub and boot priorities in order for windows to start without the need of having the flash drive connected and yet ubuntu to be bootable?

---

### Post by c0mput3r_n3rD on 2009-10-02
> **chriskin said:**
> a friend got ubuntu on a usb flash drive and windows on the primary hd
how should we set grub and boot priorities in order for windows to start without the need of having the flash drive connected and yet ubuntu to be bootable?

If you don't have Ubuntu on your HDD, then you don't need grub.  That's a matter of your BIOS checking for a bootable usb before it checks for an image on your HDD...

---

### Post by blueridgedog on 2009-10-02
If the bios can be set to boot from USB, then you should be OK without grub.

---

### Post by chriskin on 2009-10-02
well stupid question then
how does one remove grub?

---

### Post by blueridgedog on 2009-10-03
By re-installing another boot loader.  If you have XP, then you want to boot off of the CD and install the windows loader...I think the command is FIXMBR.

See:  [http://answers.google.com/answers/threadview/id/215902.html](http://answers.google.com/answers/threadview/id/215902.html)

---

