---
title: "Problems connecting parallel-port scanner with sane"
date: 2006-03-11
forum: General Help
---

### Post by Ubuntu_User on 2006-03-11
Hey all,

I'm trying to connect a UMAX Astra 2000P parallel port scanner under Breezy. I edited the dll.conf file and uncommented the umax_pp file. In the umax_pp.conf, I changed the port to auto and entered option astra 2000

My problem is when I run the sane-find-scanner program, it won't find it. I have tried running it as root and with the -p options. The verbose output gives me this error:

checking parport0... failed to open (Invalid argument)
checking parport0 (SCSI emulation)... failed to open (Device busy)

Any help would be greatly appreciated!

---

### Post by dcstar on 2006-03-11
[QUOTE=Ubuntu_User]Hey all,

I'm trying to connect a UMAX Astra 2000P parallel port scanner under Breezy. I edited the dll.conf file and uncommented the umax_pp file. In the umax_pp.conf, I changed the port to auto and entered option astra 2000

My problem is when I run the sane-find-scanner program, it won't find it. I have tried running it as root and with the -p options. The verbose output gives me this error:

checking parport0... failed to open (Invalid argument)
checking parport0 (SCSI emulation)... failed to open (Device busy)

Any help would be greatly appreciated![/QUOTE]
System-Administration-Devices and look for you printer port, have a look as to what it is called in the Advanced section.

---

