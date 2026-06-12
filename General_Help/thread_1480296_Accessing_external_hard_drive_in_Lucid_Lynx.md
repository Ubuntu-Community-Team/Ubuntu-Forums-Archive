---
title: "Accessing external hard drive in Lucid Lynx"
date: 2010-05-11
forum: General Help
---

### Post by GammaPoint on 2010-05-11
A year ago I put some stuff on my external hard drive and now I'd like to retrieve it. I've upgraded through a couple of versions of Ubuntu since then and now it doesn't work. I saw that this is a frequent problem in the forums but couldn't find a solution. Any idea how I can access my drive?

```

GP@home:~$ sudo lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 002: ID 046d:c51a Logitech, Inc. MX Revolution/G7 Cordless Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 001 Device 007: ID 0d49:7100 Maxtor** 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

---

### Post by GammaPoint on 2010-05-11
Also, I see a 'Floppy Disk' at the top menu under 'Places'. When I click on it though I get the following error message:

```
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending
```

---

### Post by 98cwitr on 2010-05-11
do you see it in the Disk Utility?

---

### Post by GammaPoint on 2010-05-11
> **98cwitr said:**
> do you see it in the Disk Utility?


Yes, it shows up in the Disk Utility. Is there something I can do with that information?

---

### Post by Delidumrul on 2010-05-24
can u paste the dmesg output here please
for floppy try 
# modprobe  -r floppy 
or you can blacklist the driver.

---

