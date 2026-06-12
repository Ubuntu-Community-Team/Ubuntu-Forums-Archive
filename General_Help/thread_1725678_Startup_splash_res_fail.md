---
title: "Startup splash res fail"
date: 2011-04-10
forum: General Help
---

### Post by vd8drum on 2011-04-10
So I installed my ATI graphics driver in Ubuntu 10.10, and it took my pretty startup splash logo away. I tweaked around with this and I got the splash back, but it's big, and terrible res.

Any help with this? I've tried startupmanager and everything Dx

---

### Post by leviathan8 on 2011-04-10
I have the fglrx driver too, and it changed my splash screen as it did to you. Though I don't really care about this.

---

### Post by vd8drum on 2011-04-11
Anyone? D:

---

### Post by Krytarik on 2011-04-11
Do you have set the desired resolution in "/etc/default/grub", like this?:
```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
[B]GRUB_GFXMODE=800x600
[/B]**GRUB_GFXPAYLOAD_LINUX=800x600**
```After doing changes there, run:
```
sudo update-grub
```Also, check these workarounds, from the readme of the Plymouth boot splash (/usr/share/doc/plymouth/README.Debian):
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
sudo update-initramfs -uAnd one more method:
[http://mikebeach.org/2010/06/nvidia-proprietary-drivers-and-low-resolution-plymouth-splash-screen/](http://mikebeach.org/2010/06/nvidia-proprietary-drivers-and-low-resolution-plymouth-splash-screen/)

Greetings.

---

