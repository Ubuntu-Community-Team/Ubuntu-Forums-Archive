---
title: "strange usb flash drive boot problem"
date: 2010-11-19
forum: General Help
---

### Post by beep_ on 2010-11-19
Hi everyone

I installed ubuntu 10.10 onto my laptop a few days ago from a usb flash drive (i have a speedstep problem as well, but i'll leave that for another thread). The flash drive that I used, prior to configuring it for booting and installing ubuntu using the Universal-USB-Installer-1.8.1.0 program, would give me a 'Disk read error has occurred...Press CTRL+ALT+DEL to restart' error if it was plugged in when I switched the laptop on.

I now want to re-install my copy of windows 7. I tried merely copying the windows files from the disk image to the flash drive, but that did not boot and start setup. I then tried one of the numerous guides available on the internet for creating bootable flash drives for installing windows 7, all of which do not boot on my laptop. However, after trying these guides and microsoft’s Windows7-USB-DVD-tool utility, my flash drive no longer gives a disk read error at boot time. Which leads me think that by formatting and recreating partitions or whatever else, something was erased from or placed onto my flash drive which does not agree with my laptop anymore.

I have tried using other flash drives as well with the internet guides and microsoft’s tool, all to no avail. I would just use my dvd drive, but it does not work and this seems to be the easier route than replacing it. My laptop is an old fujitsu-siemens m6453g model.

I would be very appreciative if someone with more experience with these things could help me solve my problem.

---

### Post by beep_ on 2010-11-21
no takers? could someone maybe shed some light on the requirements for booting of usb with regard to boot records and such, and why they might be different for an old laptop?

---

### Post by AnotherMuggle on 2010-11-21
I followed this guide a few days ago, worked perfectly for me:
[http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/)

---

### Post by beep_ on 2010-11-22
I have tried that guide and others like it, works fine on my deskop, but not on my laptop. Any other ideas?

---

### Post by AnotherMuggle on 2010-11-22
> **beep_ said:**
> I have tried that guide and others like it, works fine on my deskop, but not on my laptop. Any other ideas?

Some BIOS will just not boot from USB.  Have you checked the boot order to confirm that it is capable of booting from USB?

---

### Post by beep_ on 2010-11-22
yes booting from usb is enabled, and i have booted from the drive to install ubuntu. after i have formatted (and done other things according to the online guide) the drive to install windows, i can no longer boot from it. my original post has more details

---

### Post by AnotherMuggle on 2010-11-22
> **beep_ said:**
> yes booting from usb is enabled, and i have booted from the drive to install ubuntu. after i have formatted (and done other things according to the online guide) the drive to install windows, i can no longer boot from it. my original post has more details

OK.

Did you follow the guide I linked to, word for word, including the unusual formatting process?

The important parts are the "CLEAN" command and the "BOOTSECT.EXE /NT60 H:" command.  The first one zero's out the existing MBR and the second one creates a new, and relevant one.

If you are sure you did it exactly then I don't know what the problem could be, sorry.

---

### Post by C.S.Cameron on 2010-11-23
The flash drive needs to be formatted NTFS before copying the stuff from the DVD to it.
Then it needs to have it's boot flag set.

Gparted works for both.

If you have a CD drive Plop should boot the USB.

---

### Post by beep_ on 2010-11-23
I have followed the guide word for word, and I know I have done so correctly because I can use the drive to boot on my desktop. It's probably be some small quirk in my old laptop's bios that is causing the problem. Gparted confirms that the boot flag is set, and I cant use my dvd drive because it does not function

---

