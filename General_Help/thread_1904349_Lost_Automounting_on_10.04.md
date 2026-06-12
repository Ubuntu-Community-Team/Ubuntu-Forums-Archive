---
title: "Lost Automounting on 10.04"
date: 2012-01-04
forum: General Help
---

### Post by bmillham on 2012-01-04
I updated my kernel a while back, and since then Automounting of CD/DVD and USB devices no longer works :(

I can use Disk Utility to mount and un-mount devices still.

I've tried turning off/on Automounting in Nautilus, with no luck.

Any ideas?

Thanks!

---

### Post by Tamlynmac on 2012-01-04
Just a quick thought.

Have you checked the gnome configuration editor to assure the automount option is being cycled by Nautilus?

"system tools/configuration editor/apps/nautilus/preferences/media_automount"



* After updating your kernel, I'll assume you have rebooted.

Good Luck

---

### Post by bmillham on 2012-01-04
I double checked the media_automount option, and it is on. I did turn it off, log out, and turned it back on, (logged off/on again) still no luck.

And lol, yes, I rebooted after updating the kernel :)

Is there supposed to be an entry in /etc/fstab for the USB and CD?

---

### Post by Tamlynmac on 2012-01-04
> bmillham
Is there supposed to be an entry in /etc/fstab for the USB and CD?

I see nothing in my fstab that's associated with cd or usb. I'm  wondering if it might make sense to reinstall the old kernel. Perhaps,  the issues resides in the kernel as that's when you started experiencing  it. Or maybe uninstall Nautilus and re-install it (a lost lib or link).

It's odd that your able to mount the devices with the utility, but not  with Nautilus. Hopefully, someone else may have experienced this issue  and will respond.

Good Luck

---

### Post by bmillham on 2012-01-04
Trying to uninstall Nautilus looks like a bad idea. It wants to uninstall ubuntu-desktop when I do that... And I don't really think I want to remove the desktop :D

I've been thinking about what happened just before this problem appeared, and realized that I had installed 'Audio CD Extractor' also. I'm wondering if that did something to kill automounting.

I had tried going back to the old kernel when this first happened, but no luck there.

Thanks for the help!

---

