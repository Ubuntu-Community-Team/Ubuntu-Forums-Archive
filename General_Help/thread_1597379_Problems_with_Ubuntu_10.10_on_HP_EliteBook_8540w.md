---
title: "Problems with Ubuntu 10.10 on HP EliteBook 8540w"
date: 2010-10-15
forum: General Help
---

### Post by jancogo on 2010-10-15
I just got a new HP EliteBook 8540w laptop at work and tried to install the latest Ubuntu on it. The install finished and once I rebooted I managed to log in. The next time I rebooted I was met with the following line after grub:

[drm] nouveau 0000:01:00.0: Poninter to BIT loadval table invalid

And it just hangs there. I have tried rebooting several times but it stops here every time. Anyone else experiencing this problem?

---

### Post by Hippytaff on 2010-10-15
Might be something to do with Nvidia? drivers etc?
 
Might be worth booting from live cd and see if the same problem occurs

---

### Post by jancogo on 2010-10-15
The live cd seems to be working. If I reboot several times I manage to get by the error message, and can log into the system. Seems to me like this might be some hardware issues since the error disappears once in a while. Any tips on how to debug?

---

### Post by okdok on 2010-12-16
Some errors still exist with the BIOS and are being addressed.

In the mean time the initial load can be accomplished by using an alternatives disk as opposed to the normal live cd. When preparing to install, set other options to 'nomodeset' and you will be able to boot into the OS when complete and grab updates and NVIDIA drivers.

Additionally, some are noticing the first core getting pegged at near 100% full time. This can be mitigated by adding the following to rc.local:

```

echo disable > /sys/firmware/acpi/interrupts/gpe01

```

---

### Post by jancogo on 2011-01-26
I'm still having issues booting when using the open source nvidia driver. Why am I using these you ask? Well, when I use the proprietary nvidia driver, the gnome-settings-daemon crashes on boot, and the theme gets all f***** up, and there are problems using external monitors and so forth.

---

### Post by ltholmes on 2011-04-08
i am wanting to install ubuntu 10.10 on my hp 8540w with an nvidia vga because cannot resolve wireless connection in opensuse 11.2 but wondering if your issue was ever resolved.

thanks for any info/insight 

-Lori

---

### Post by jancogo on 2011-04-13
This issue is still not resolved. When I boot using the open source driver, it hangs 3 out of 4 times. When it finally boots, the gnome theme looks fine.

If I use the official driver, the machine boots every time, but the theme is not applied (looks like the gnome-settings-daemon still crashes).

---

