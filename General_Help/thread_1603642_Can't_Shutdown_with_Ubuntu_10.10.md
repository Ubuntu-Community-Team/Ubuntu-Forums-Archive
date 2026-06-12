---
title: "Can't Shutdown with Ubuntu 10.10"
date: 2010-10-23
forum: General Help
---

### Post by kevin11951 on 2010-10-23
When I press the "Shut Down" button in Gnome, it does nothing.  When I press "Log Out" it also does nothing.  For the past couple weeks I have been forced to type "sudo halt" into the terminal every time I want to shut down.

I have checked all the usual logs (syslog/dmsg/Xorg/gdm) and can't find anything applicable.

I have used Linux (mostly Debian) for a few years now, mostly via CLI in servers, and I have no idea how to fix this... :(

---

### Post by mklinux on 2010-10-23
I tried the following, but it's still not working...:(

RePost of solution:
The RT3090 wireless was the problem. To fix it, you can install the DKMS kernel module package containing ralink’s proprietary source drivers. I just downloaded the prebuilt DKMS package on that page, I didn’t build it myself. Then I blacklisted the OSS ralink modules:

Appending to /etc/modprobe.d/blacklist.conf

# blacklist other Ralink modules in favour of 3090 DKMS mod
blacklist rt2860sta
blacklist rt2870sta
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb"

---

### Post by mklinux on 2010-10-23
Actually, I'm an idiot. I tried it again and it worked. Just edit out the " on the end. So this does work :)!!! &#50500;&#49912;!

# blacklist other Ralink modules in favour of 3090 DKMS mod
blacklist rt2860sta
blacklist rt2870sta
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb

---

### Post by kevin11951 on 2010-10-24
> **mklinux said:**
> Actually, I'm an idiot. I tried it again and it worked. Just edit out the " on the end. So this does work :)!!! &#50500;&#49912;!

# blacklist other Ralink modules in favour of 3090 DKMS mod
blacklist rt2860sta
blacklist rt2870sta
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb

That fixed it, thank you!

---

### Post by jur9en on 2010-10-25
Same issue with my EeePC 1001HA. Wouldn't shut down after upgrading to Ubuntu 10.10.
This solution worked, because it was caused by the wireless as well.

See thread: [http://ubuntuforums.org/showthread.p...6#post10012136]("http://ubuntuforums.org/showthread.php?p=10012136#post10012136")
for more details on how to install the RT3090 DKMS package from Markus-tisoft.

---

### Post by odror on 2010-10-29
This did not work for me. I have dell xps 420 desktop.

Any other ideas how to find the problem. 

restart works find, but shutdown does not. what is the difference??

Thanks

---

