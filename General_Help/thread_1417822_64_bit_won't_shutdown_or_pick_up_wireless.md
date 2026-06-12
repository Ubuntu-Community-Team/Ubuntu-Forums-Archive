---
title: "64 bit won't shutdown or pick up wireless"
date: 2010-02-27
forum: General Help
---

### Post by lowtech9 on 2010-02-27
OK, read loads of threads . . . tried a few diff workarounds, still no joy.
I'm running an HP Pavillion ZV6000, AMD 64 Athlon.
 I think that I'm not getting wireless because it never really shuts down. I've tried shutting down from the term (what I was used to from Damn Small) and it drops the window manager and then freezes on the black screen . . . I then have to do a hard shutdown (holding the power button).
 I've tried making sure that I don't have a USB stick in . . . shutdown wireless moduals, still the same.
 I'm starting to forget my keyboard commands, being that I am having to use windows to get on-line . . . like now! Help me get off XP!

   LowTech9

---

### Post by Scunizi on 2010-02-27
you might need to acpi=off in the kernel line of grub (1 or 2).

To shut down try sudo shutdown now and see if that works.

---

### Post by lowtech9 on 2010-02-27
That is how I've always shutdown . . . no good, that or "sudo shutdown -r now"
I've tried adding acpi=off in the menu that I get when booting up (I'm doing a dual-boot system w/ windows) No good.

---

### Post by lowtech9 on 2010-02-28
I'm now finding that I need to update the firmware (b43), maybe that's why I'm not on-line? How do I download it on windows and then install it on ubuntu?
 Still not finding a way to make it do a full shutdown.

---

### Post by Scunizi on 2010-02-28
You can find packages on [http://packages.ubuntu.com](http://packages.ubuntu.com) .. Some motherboards just have strange issues.. I have an XFX Gforce 8200 board with an AMD5300 64bit processor and onboard nvidia graphics.  Just to boot past the main menu on the live cd I need to add pci=nomsi to the kernel line... then after install put that same command in the same place in grub to make it persistent.

Wireless is another issue entirely.. Could just be the chipset, could be network manager being quirky.  If you have any type of encryption on your wireless network try turning it off and broadcasting the ssid and see if you can connect..

---

