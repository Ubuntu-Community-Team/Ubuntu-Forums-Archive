---
title: "Safely remove, not just unmount?"
date: 2011-03-12
forum: General Help
---

### Post by hakermania on 2011-03-12
My USB stick has a light at the bask, showing when data are passing through...
With umount the USB stick's light will still be on, and in computer:/// location I can still see the USB stick. But if I choose safely remove drive, the light will turn off and I would see nothing in computer:/// about my USB.
So, I prefer Safely Remove than Unmount, for these few reasons.
What is the command to safely remove?

---

### Post by turtle153 on 2011-03-12
You need to **eject** the drive, therefore I believe **sudo eject /dev/[name]** will do it.

---

### Post by turtle153 on 2011-03-12
Or perhaps it's **sudo umount -l /media/[name]**.

---

### Post by jerome1232 on 2011-03-12
afaik, unmount is a safe remove, it finishes up any writes to the disk then unmounts it.


It will not do an unclean unmount if that makes any sense.

---

### Post by stoneage on 2011-03-12
Safely remove is intended for external drives. It unmounts and shuts off the power. Apparently it was introduced because some(though rare) drives need to be removed this way to ensure a clean removal.

There is no reason not to use it for a usb, though in those circumstances unmount is just fine.

If you unmount, the power is still on and you can remount it. If you safely remove, it is powered off, and you have to remove and reinsert to mount it again.

---

