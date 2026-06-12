---
title: "My computer boots funny"
date: 2011-03-02
forum: General Help
---

### Post by booterror on 2011-03-02
I just got a new laptop and installed ubuntu 10.10 64 bit on it. I ran all the updates and activated the nVidia driver and restarted. It boots really slow and the splash screen is all weird and text based. How do I make it boot faster and possibly get it back to the normal splash screen?

---

### Post by Frogs Hair on 2011-03-02
I don't know why it boots slow , but proprietary drivers will cause problems with your splash screen , It is something I live with also.

There are some fixes on the web if you search . Check System > Preferences > Start Up Applications and see if you are starting any unneeded programs at boot.

I need Nvidia drivers for my dock and Compiz , so live with the splash screen.

---

### Post by Krytarik on 2011-03-02
As for the splash screen, try this workarounds, from the plymouth readme (/usr/share/doc/plymouth/README.Debian):
> High-color graphics on nVidia, ATI and other cards
--------------------------------------------------

Our default configuration uses low-color graphics on cards or drivers
for which "Kernel Mode Setting" (in-kernel graphics drivers) are not
available.

This is because the driver that permits high-color graphics tends to
cause issues with suspend and resume, and we opted to prefer that
working.

For nVidia and ATI users, the default "nouveau" and "radeon"
drivers are Kernel Mode Setting enabled, but do not always
provide 3D capability at the current time. By switching to
using the restricted/non-free nvidia-glx or fglrx drivers,
you will gain 3D capability at the loss of a high-color
splash screen.

You can however chose to enable high-color (and resolution) console
if you find it doesn't affect suspend/resume for you, or you don't
use that feature.

There are various methods of doing this, the most robust is the
following four steps:

Append video=vesafb to the GRUB_CMDLINE_LINUX_DEFAULT in
/etc/default/grub
sudo update-grub

echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u

As for the slow startup: "Startup Applications" are run *after* you see at least your desktop background. If you mean the actual boot-up process, like I guess, check the log in "/var/log/messages".

---

### Post by booterror on 2011-03-02
I found something in the wiki on how to fix it, and I think I might have it fixed. I don't know I haven't rebooted yet. I have discovered however that my sound isn't working. When I try to play music it just makes a soft droning sound. Kinda like old computer modems but softer sounding.

---

### Post by Krytarik on 2011-03-02
> **booterror said:**
> I found something in the wiki on how to fix it, and I think I might have it fixed. I don't know I haven't rebooted yet. I have discovered however that my sound isn't working. When I try to play music it just makes a soft droning sound. Kinda like old computer modems but softer sounding.
Check if the boot issue is fixed when you boot the next time.
If it is, but the sound issue persists, please start another thread about it.

---

