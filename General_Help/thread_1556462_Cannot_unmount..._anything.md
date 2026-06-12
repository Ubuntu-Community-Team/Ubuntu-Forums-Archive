---
title: "Cannot unmount... anything?"
date: 2010-08-19
forum: General Help
---

### Post by Roasted on 2010-08-19
I installed KDE 4.4 through Ubuntu's repos and then upgraded to 4.5 via backport PPA. I am unable to unmount any USB device. It keeps saying it's in use by another application. Even if I plug it in and do nothing, but then try to unmount, it gives me this error.

What gives?

---

### Post by Ubuntiac on 2010-08-19
Sometimes I find that when I mount a drive with Dolphin and then close Dolphin that the lock isn't given back.

Do you get this when doing the following?

1. Make sure no apps are open (especially Dolphin)
2. Insert your usb drive
3. Mount your device with the device notifier (the thing that pops up telling you the usb stick has been plugged in). Choose the option *just to mount* not to open dolphin
4. Try unmounting from the device notifier.


I'd also ask if you're using auto mounting in System Settings -> Removable media.

---

### Post by Roasted on 2010-08-19
No matter what I do it yells at me, forcing me to have to just rip out the USB device.

The only thing that works is if I use terminal to unmount, which isn't a big deal for me since I'm kind of a terminal junkie, but seriously - with Linux on your work laptop, sometimes terminal for simple things isn't that easy to do.

I'm simply test driving KDE 4.5 on an Ubuntu 10.04 system, with intention of moving to it entirely if I don't run into any issues. The future for KDE in this case is mighty grim. :(

---

### Post by Ubuntiac on 2010-08-20
So just to be absolutely clear:

1. Did you try the sequence I suggested above and
2. Are you using Automount in Removable Devices?

---

### Post by Roasted on 2010-08-20
> **Ubuntiac said:**
> So just to be absolutely clear:

1. Did you try the sequence I suggested above and
2. Are you using Automount in Removable Devices?

I've tried just plugging it in and browsing through dolphin.
I've tried mounting it via dolphin.
I've tried plugging it in, touching nothing, and simply clicking eject, both in dolphin and in the removable devices widget.

All of which error out saying it cannot unmount, regardless of the pattern I do it in. 

It's not a big deal though. I've uninstalled KDE. :(

(but hey, if you know why I'm having weird kde-like fonts in thunderbird and firefox even though I uninstalled kubuntu-desktop and ran puregnome, that'd be great! can't seem to revert these apps back to default font style)

---

### Post by Ubuntiac on 2010-08-20
Dunno. I suspect that's something to be changed in Gnome / FF / Thunderbird - which puts it out of my area of knowledge...

---

### Post by dino99 on 2010-08-20
maybe give mountmanager a try: set your prefs with all your partitions and devices

---

