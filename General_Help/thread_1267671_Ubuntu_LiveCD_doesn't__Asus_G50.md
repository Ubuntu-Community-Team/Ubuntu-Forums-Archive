---
title: "Ubuntu LiveCD doesn't  Asus G50"
date: 2009-09-16
forum: General Help
---

### Post by Laughing Cheese on 2009-09-16
I recently got an Asus G50vt series laptop and it has a second partition on the hard drive which is presumably to store data when the techs are working on it but I back up with external hard drives so I'm not worried about that.

Therefore I would like to use the extra partition to install Ubuntu on, however the LiveCD wouldn't start when I rebooted the computer so I'm wondering if that means it has compatibility/driver issues with Ubuntu/Linux?


EDIT: Can a mod change the title to "Ubuntu Live CD doesn't load on Asus G50"? Realized I didn't finish the sentence there. :p

Thanks

LC

---

### Post by QIII on 2009-09-16
The LiveCD wouldn't start, but instead the computer booted to the "other" (hack, spit) OS?

---

### Post by Laughing Cheese on 2009-09-16
> **QIII said:**
> The LiveCD wouldn't start, but instead the computer booted to the "other" (hack, spit) OS?

Yes, it booted normally into Vista as if there was no disc in it at all, in other words, the Live CD was totally undetected. 


(I only have Vista because it came with my laptop. :p)

Sorry I wasn't clear on that.

---

### Post by QIII on 2009-09-16
Is your BIOS configured to boot first from CD?

---

### Post by themagiczebra on 2009-09-16
If your boot order is set to have CD boot before HD and you're getting some weird error while trying to install Ubuntu 9.04 via Live CD (like, "I/O failure" or "Couldn't read disc"), then I might know what the problem is.

I had an issue yesterday while I attempted to install Ubuntu JJ. The problem was my CD/DVD drive's lack of compatibility with the Ubuntu. To work around this, I would suggest doing the following:

1. Download a copy of the Ubuntu 9.04 iso
2. Acquire a USB flash drive with at least 1 gig of memory.
3. Download and run Unetbootin. It will let you turn your flash drive into an Ubuntu Live CD in which you can install Ubuntu from your flash drive instead of CD.

You're going to need to format your USB flash drive before doing this. Just back up any files you want to keep because doing this will wipe the drive. Assuming you're doing this in Vista, go to Computer, then right click on the USB device and choose Format. Select FAT32, and check Quick Format. 

When it's done, load up Unetbootin, select the ISO option, and navigate to the ISO. Make sure you select the right USB drive to install it on.

Once Unetbootin is finished it will want you to restart your computer. Do it, then press and hold the Delete key (or whatever key you usually use to enter BIOS). Change your boot order so that USB Devices boot BEFORE your HD. Once you get that, save and exit.

---

### Post by Laughing Cheese on 2009-09-16
> **QIII said:**
> Is your BIOS configured to boot first from CD?

I'd have to check; however, the reason I'm posting this is because it works fine on my desktop, but I guess it might not be compatible with my disc drive.

> **themagiczebra said:**
> If your boot order is set to have CD boot before HD and you're getting some weird error while trying to install Ubuntu 9.04 via Live CD (like, "I/O failure" or "Couldn't read disc"), then I might know what the problem is.

No error, it simply boots normally into Vista like its not even there.

And again, I'd have to check to see what the BIOS settings are.


> I had an issue yesterday while I attempted to install Ubuntu JJ. The problem was my CD/DVD drive's lack of compatibility with the Ubuntu. To work around this, I would suggest doing the following:

1. Download a copy of the Ubuntu 9.04 iso
2. Acquire a USB flash drive with at least 1 gig of memory.
3. Download and run Unetbootin. It will let you turn your flash drive into an Ubuntu Live CD in which you can install Ubuntu from your flash drive instead of CD.


I've tried Unetbootin before and it didn't seem to work; more likely though I probably just didn't know what I was doing.

I'll give it another look.

> You're going to need to format your USB flash drive before doing this. Just back up any files you want to keep because doing this will wipe the drive. Assuming you're doing this in Vista, go to Computer, then right click on the USB device and choose Format. Select FAT32, and check Quick Format.


No problem there, my flash drive doesn't have anything important on it anyways. 

> When it's done, load up Unetbootin, select the ISO option, and navigate to the ISO. Make sure you select the right USB drive to install it on.

Once Unetbootin is finished it will want you to restart your computer. Do it, then press and hold the Delete key (or whatever key you usually use to enter BIOS). Change your boot order so that USB Devices boot BEFORE your HD. Once you get that, save and exit.


Thanks, I'll try that.

---

