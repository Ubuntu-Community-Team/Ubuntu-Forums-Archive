---
title: "Memtest hang and &quot;Unable to find a medium containing a live file system&quot; from USB"
date: 2011-03-17
forum: General Help
---

### Post by Quatrix on 2011-03-17
I'm setting up a new PC with ASUS P8P67 Pro motherboard and 2600K CPU.  I used Universal-USB-Installer-1.8.3.6 to install the Ubuntu 10.10 live "CD" to a USB drive so I could test some stuff before moving my existing hard drive over.  It boots fine on my current PC.

The new PC is a different story.  Memtest 4.10 hangs on startup, and Ubuntu drops to a busybox prompt with the error "Unable to find a medium containing a live file system".  If I install the stand-alone Memtest 4.20 on a USB drive, however, it runs perfectly and the memory checks out.  I can also boot into Acronis True Image and Disk Director from a USB drive.  That leads me to believe that the hardware is fine and there's something screwy with Ubuntu 10.10 or the USB installer.

I don't have an optical drive in the new PC yet, so booting Ubuntu from a CD isn't an option.

Any ideas?  Could the "unable to find a medium" error occur because I have no drives attached?

---

### Post by Quatrix on 2011-03-18
Here's an update.  Today I moved my hard drive to the new PC and booted both XP and 7 without a significant hitch.  I also tried a different USB installer and it didn't make a difference, so it still seems like there's a problem with the 10.10 LiveCD.  Anyway, not really concerned now that Windows and GRUB are working, though I haven't yet tried booting Ubuntu 9.

---

### Post by psusi on 2011-03-18
I have the same board and had the same problem with memtest and had to go get their latest version.  Don't have any trouble booting from the live USB though.  I did update the bios on it though, maybe you should try that.

Also, are you plugging the stick into the USB3 port, or the USB2 port?

---

### Post by Quatrix on 2011-03-18
Thanks for responding.  I can boot into 7, XP, and Ubuntu 9.04 with no trouble now, so I'm not concerned about the 10.10 flash drive now.  Read on if you're interested anyway.

Now I see in the Memtest change log that Sandy Bridge support was added in 4.20, so that explains that.  I'm already using the latest (1305) BIOS.  I wasn't paying much attention to the ports, but I tried enough times that I must have used both USB 2.0 and 3.0.  One thing I noticed with the LiveCD is that the graphics don't look right.  The boot menu (boot Ubuntu from LiveCD, Memtest, etc.) is in black and white, for example.  I tried other distributions such as Mythbuntu with exactly the same result.

---

### Post by Quatrix on 2011-03-18
Never mind, mystery solved.  Once I had a hard drive attached, the error went away and 10.10 on the USB drive booted up normally.  It's strange that the LiveCD would require permanent storage to be installed, but whatever.  Maybe this will help someone else later.  Thanks.

---

