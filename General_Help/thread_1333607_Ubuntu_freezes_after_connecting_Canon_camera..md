---
title: "Ubuntu freezes after connecting Canon camera."
date: 2009-11-21
forum: General Help
---

### Post by Ubu4moi on 2009-11-21
I'm running Ubuntu Ultimate Edition 2.0 64 bit on an HP Pavilion Athlon X2. After I connect the camera via USB and try to copy pics to a folder the computer just stops working right. It hangs on that action and everything gets too slow. Feels like Windows, please help. Any other application also hangs and I have to re-boot the system. This is not right.

---

### Post by AlphaLexman on 2009-11-21
Are you connecting the camera directly or just the compact flash/memory card?
Is the camera setup to be read as a camera or as a usb flash drive?

---

### Post by Ubu4moi on 2009-11-21
I'm connecting the camera directly to the USB. The camera doesn't have a setting for camera or usb. When I connect it it shows as a camera(icon) on Nautilus file manager and it opens as a regular folder. Is when I try to copy the pics that everything freezes. It even shows the pics as thumbnails. Is this a bug?

---

### Post by AlphaLexman on 2009-11-21
What camera model is it? Does it have a flash card?

Post the result of :

```
lsusb
```

with the camera plugged in.

What software are using to transfer your pics from your camera to your harddrive? Nautilus is not the best choice if your camera is not in usb mode. Do you have F-Spot or Digikam installed? They can read many popular/common cameras.

---

### Post by Ubu4moi on 2009-11-21
> **AlphaLexman said:**
> What camera model is it? Does it have a flash card?

Post the result of :

```
lsusb
```

with the camera plugged in.

What software are using to transfer your pics from your camera to your harddrive? Nautilus is not the best choice if your camera is not in usb mode. Do you have F-Spot or Digikam installed? They can read many popular/common cameras.
result:
Bus 002 Device 003: ID 04a9:3148 Canon, Inc. 
Bus 002 Device 002: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

F-Spot cannot connect to camera; it says that it cannot lock the device.

---

### Post by AlphaLexman on 2009-11-21
Well obviously, the kernel and your usb has identified the camera is attached to your machine. So it's there. It just might be a transfer problem.

Are your pics in jpg or crw [canon raw] format? CRW files are much larger than compressed jpeg's, but offer more post-processing options.

I still ask if you have a memory card that you could plug in directly?

How many pics are you trying to transfer at once? A lot or one?

How much memory / processor power do you have? Is ubuntu frozen or just slow?

The key to problem solving is to eliminate all possibilities until a solution is found.

---

