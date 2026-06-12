---
title: "Mounted Drives not showing up on desktop"
date: 2010-02-26
forum: General Help
---

### Post by helblaze on 2010-02-26
My laptop stopped mounting all usb devices (netbook, so no optical drive), I managed to get it to start mounting them again, but I can't figure out how to get them to show up on my desktop.

on a side note in grub I have both ubuntu, linux 2.6.31-19-generic and ubuntu, linux 2.6.31-14-generic

How do I remove the older boot options?

---

### Post by johngreth on 2010-02-26
I don't know about the drive mounting, but you can remove the grub entries by uninstalling the old linux header and linux kernel packages from the synaptic package manager. Just be careful you only uninstall the packages marked 2.6.31-14.

---

### Post by egalvan on 2010-02-26
If  a USB device has a drive label, then it will automatically show up on the desktop.

If any device is mounted at /media, the it will automatically show up on the desktop.

Devices mounted at /mnt do not show on the desktop.

---

### Post by helblaze on 2010-02-26
> **egalvan said:**
> If  a USB device has a drive label, then it will automatically show up on the desktop.

If any device is mounted at /media, the it will automatically show up on the desktop.

Devices mounted at /mnt do not show on the desktop.

my drives are showing up inside of media not mnt, but aren't showing up on the desktop (yes all of my usb's are named)

---

### Post by dpwilson on 2010-02-27
install gconf-editor from synaptic

run it and go to  */apps/nautilus/desktop/volumes_visible* and make sure it is checked

---

### Post by helblaze on 2010-02-27
> **dpwilson said:**
> install gconf-editor from synaptic

run it and go to  */apps/nautilus/desktop/volumes_visible* and make sure it is checked

Thanks that's exactly what was wrong

---

### Post by dakers001 on 2010-10-26
I needed just the opposite but the advice worked, so thanks a lot!

---

