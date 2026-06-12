---
title: "VirtualBox from USB drive?"
date: 2012-06-18
forum: General Help
---

### Post by qwertyjjj on 2012-06-18
Will VirtualBox work from a USB drive or will it be too slow for IO speeds?

---

### Post by qwertyjjj on 2012-06-18
any ideas?

---

### Post by Bouvet on 2012-06-18
I have VB on my lap top and desk top and love them both. But I'm not 
sure about running it from a USB drive. Surely there are videos addressing 
this? Good luck and let us know.

---

### Post by imachavel on 2012-06-18
I myself have used virtual box numerous times, and LOVE virtual box. But have never tried running it from a usb. I don't see why it wouldn't work, at long as the usb device is mounted. I've never tried running any app from a flash drive. I've only used a flash drive as a back up or to transfer files. Installed an OS on a flash drive once, then no computer I used it on could boot to it from the bios. Don't know why, I used unetbootin. Good luck with virtual box.

If you have any questions about configuring filters or setting up memory or drives or devices or hard ware acceleration for virtual box, come ask here. Best of luck

---

### Post by sudodus on 2012-06-18
> **qwertyjjj said:**
> Will VirtualBox work from a USB drive or will it be too slow for IO speeds?
Do you mean that only the VirtualBox file-system and machine files should be on a USB drive?

Or do you mean that the host operating system should be on a USB drive? In that case, a persistent live system or 'installed the normal way' but to a USB drive instead of an internal drive?

Do you mean a USB hard disk drive or a flash drive?

It is slower to send data via USB 2.0 than via SATA or PATA (IDE). USB 3 is much faster than USB 2.0, but I don't think you can boot from it.

USB flash drives are slower than USB hard disk drives because the flash is slower than the USB. So if you think of a flash drive, get a fast one, for example a USB 3 flash drive, even if you intend to connect it to a USB 2.0 port.

Anyway, I think it is possible to do it in many ways, but a bit slow. It is worth testing, maybe it will be fast enough for you.

---

### Post by haqking on 2012-06-18
[http://www.vbox.me/](http://www.vbox.me/)

and

[http://www.pendrivelinux.com/search/Portable+Ubuntu+Linux/](http://www.pendrivelinux.com/search/Portable+Ubuntu+Linux/)

---

### Post by qwertyjjj on 2012-06-19
> **haqking said:**
> [http://www.vbox.me/](http://www.vbox.me/)

and

[http://www.pendrivelinux.com/search/Portable+Ubuntu+Linux/](http://www.pendrivelinux.com/search/Portable+Ubuntu+Linux/)

No, I mean store the files on a USB but run it from a laptop system.
Actually, I will be running Ubuntu from a pen drive but want to run VB from data on a separate USB drive.

---

### Post by sudodus on 2012-06-19
> **qwertyjjj said:**
> No, I mean store the files on a USB but run it from a laptop system.
Actually, I will be running Ubuntu from a pen drive but want to run VB from data on a separate USB drive.
Yes, I think that would be possible. I have my VirtualBox on a separate data partition (with ext3 file system). I think I made some symbolic links when I moved my installation from the system partition (It was years ago). And it should work with a partition on another drive as well. It might be slow, but it is definitely worth testing.

---

### Post by haqking on 2012-06-19
> **qwertyjjj said:**
> No, I mean store the files on a USB but run it from a laptop system.
Actually, I will be running Ubuntu from a pen drive but want to run VB from data on a separate USB drive.

Yes i do that for all my VM's (about 2 TB worth) so i can share them easy between my desktop and laptop, I dont notice any issues.

Peace

---

