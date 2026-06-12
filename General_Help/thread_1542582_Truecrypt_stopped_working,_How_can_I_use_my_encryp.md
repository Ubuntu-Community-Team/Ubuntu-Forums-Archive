---
title: "Truecrypt stopped working, How can I use my encrypted flash drive without it?"
date: 2010-07-30
forum: General Help
---

### Post by Mr_VeRiTy on 2010-07-30
Hi, I installed truecrypt (thee GUI version) a short while ago, and it worked fine until now. Yesterday I took my encrypted flash drive out of my computer without dismounting it using truecrypt, and this seems to have angered it, when I start truecrypt it says that my flash drive is already mounted (which it isn't) and If I try to unmount it truecrypt crashes. Is there a way I can fix this? Or if not, how can I decrypt (or format) my flash drive to make it usable again?

If you need more info just ask.

EDIT: I forgot to add that when truecrypt starts up I get the error:
```
Deleted stale lock file '/home/luke/.TrueCrypt-lock-luke'.
```

---

### Post by mr clark25 on 2010-07-30
if you dont need to save whats on the usb drive, you should be able to format it using gparted. if gparted cant find the drive, it is probably broken...

---

### Post by Mr_VeRiTy on 2010-07-30
> **mr clark25 said:**
> if you dont need to save whats on the usb drive, you should be able to format it using gparted. if gparted cant find the drive, it is probably broken...
I can't use gparted as the device is only recognized if I mount it using truecrypt, even when I had it working, I think it's a "hidden" partition (although that wasn't my intention)

---

### Post by nerdy_kid on 2010-07-30
reboot and try again?

---

### Post by Mr_VeRiTy on 2010-07-30
> **nerdy_kid said:**
> reboot and try again?
Wow, that actually worked (theres a first.) thanks.

---

### Post by nerdy_kid on 2010-07-31
> **Mr_VeRiTy said:**
> Wow, that actually worked (theres a first.) thanks.

lol no prob :)

---

