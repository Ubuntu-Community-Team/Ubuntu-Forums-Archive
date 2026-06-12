---
title: "drivers for radeon HD 2400"
date: 2009-06-29
forum: General Help
---

### Post by enoac on 2009-06-29
i just got an ATI radeon HD 2400 pro but i cant really  use it. i cant find drivers for it. there is a proprietary driver for it that ubuntu finds and shows me but when i tell it to activate it, it wont install or activate or anything! i have installed anything to do with an ati graphics card through the synaptic package manager but still nothing. what should i do?

---

### Post by cottfcfan on 2009-06-30
Try installing the latest driver from the ATI website, the 9.6 driver is there with full instructions.
Works fine for me, and i use the same HD2400.

---

### Post by enoac on 2009-06-30
for some reason i cant get the driver to load when i do as instructed it tell me this 
```
sh: Can't open ./ati-driver-installer-9-5-x86.x86_64.run

```

---

### Post by enoac on 2009-06-30
> **enoac said:**
> for some reason i cant get the driver to load when i do as instructed it tell me this 
```
sh: Can't open ./ati-driver-installer-9-5-x86.x86_64.run

```

i finaly got it to try to run it and then this is what it says ```
Created directory fglrx-install.Dn6986
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.62......
......................................................
.......................................................
...................................................Extraction failed.
.Signal caught, cleaning up

```

am i missing something needed to install it?

---

### Post by cottfcfan on 2009-07-01
You need to change the installer to -9-6 instead of -9-5 as ita later driver.
You also need to prefix it with "Sudo"

---

### Post by Legace on 2009-07-01
Follow instructions in:
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by The_Mangler on 2009-07-04
I have Ubuntu 64 bit and a radeon HD 2400 using a dvi to hdmi cable. I've tried first to use the driver from System->Administration->Hardware Drivers but it gave me some problems. Then I deactivated it and installed the driver downloaded from [http://support.amd.com/us/gpudownload/Pages/index.aspx]("http://support.amd.com/us/gpudownload/Pages/index.aspx") and followed the instructions you can find there, it worked like a charm ! Before with glxgears I had 300 FPS now I have 2300 FPS, I'm really amazed \\:D/

The only problem I still have is that at the login window the characters size is huge, I guess 72 points. How to resolve this problem ?

---

### Post by hj_ebfe on 2010-02-03
AMD came out with a new driver for the Radeon HD 2400 xt.  [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.1&lang=us&rev=10.1&ostype=Linux%20x86](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.1&lang=us&rev=10.1&ostype=Linux%20x86)  Installer instructions are also available on the same page. This worked perfectly for me though it did not seem to be happy when I ran it from a usb key. It complained about needing to chgrp or chown.  Good luck

---

