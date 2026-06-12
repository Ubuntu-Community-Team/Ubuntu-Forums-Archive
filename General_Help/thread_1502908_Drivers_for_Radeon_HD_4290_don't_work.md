---
title: "Drivers for Radeon HD 4290 don't work"
date: 2010-06-06
forum: General Help
---

### Post by crazyfuturamanoob on 2010-06-06
Edit: _**You shouldn't read this thread because the problem is solved already.**_

I just built a new PC and installed Kubuntu 10.04 from the Alternate CD.
[list]
[*]Asus M4A89GTD PRO/USB3
[*]Integrated ATI Radeon HD 4290
[*]AMD Phenom II X6 1055T
[/list]

I downloaded the proprietary ATI driver installer from here: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English)

I ran these commands:
```

sudo apt-get purge fglrx*
sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx
cd Downloads/
chmod +x ati-driver-installer-10-5-x86.x86_64.run
sudo sh ./ati-driver-installer-10-5-x86.x86_64.run
sudo aticonfig --initial
sudo reboot now

```

After booting up, X wouldn't start. I ran some more commands:
```

cat /var/log/Xorg.0.log|less
sudo cp /var/log/Xorg.0.log ~/Documents/Xorg.0.log.atiDriver
cd /etc/X11/
sudo mv xorg.conf _xorg.conf
startx

```

Now I'm running X server without the ATI driver, and writing this message.

I uploaded _xorg.conf and Xorg.0.log.atiDriver as attachments (renamed them because this stupid forum does not allow uploading other text files than .txt)

```

arho@tehomylly:~/Documents/upload$ cat Xorg.0.log.txt |grep '(EE)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) fglrx(0): Hasn't established DRM connection
(EE) fglrx(0): Hasn't established DRM connection
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(EE) fglrx(0): Failed to map FB memory
(EE) fglrx(0): firegl_SetSuspendResumeState FAILED -9.

```

```

arho@tehomylly:~/Documents/upload$ cat Xorg.0.log.txt |grep '(WW)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) Falling back to old probe method for fglrx
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:5:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Hasn't establisted DRM connection
(WW) fglrx(0): No DRM connection for driver fglrx.
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

I tried googling but didn't find anything helpful. How can I get the driver working?

---

### Post by crazyfuturamanoob on 2010-06-06
I just found out that driver 10.5 does not support my HD 4290. :mad:

Version 9.3 supports HD 4290 but only supports Ubuntu 9.04 (and older). :mad: :mad:

(I have Kubuntu 10.04 installed on this machine)

Edit:
Here's ATI/AMD website for drivers: [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
The driver in Linux x86_64->Integrated/Motherboard->Radeon HD 4290 is 10.5 which does not support this video card! WTF?

How to get hardware acceleration to work?

Edit2:
I messed with hardware drivers until my system was completely unbootable and unusable. Then I reinstalled Kubuntu, and 3D acceleration just started magically working. :D :D :D :D :D

---

### Post by daasdingo on 2010-06-15
just for the information,
i have nearly the exact same hardware(Gigabyte instead of ASUS board, but same chipset).

The 10.5  driver from the AMD website DOES work for me.
```

~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4290
OpenGL version string: 3.3.9836 Compatibility Profile Context

```
from gui:
Catalyst™ Version 10.5

---

### Post by crazyfuturamanoob on 2010-06-15
I have Catalyst 10.5 too (from AMD website). I just don't know why it didn't work before re-installing Kubuntu.

---

### Post by derlok on 2010-06-17
now new version 10.6 for x86 and x86_64 are available on [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

---

