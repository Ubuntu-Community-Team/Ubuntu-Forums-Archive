---
title: "Turn Off Firewire"
date: 2010-12-12
forum: General Help
---

### Post by spikoley on 2010-12-12
When I boot it takes about 5 seconds for the firewire device (fw0) to load.  I don't use firewire and I would like to disable it to help improve my boot time.  My BIOS doesn't have an option to turn it off.  Is there a way I can turn it off in Ubuntu?

---

### Post by tgalati4 on 2010-12-12
You would have to search for a kernel command switch to put into your grub2 line.  Something like "noeee1394" or "nofirewire"

---

### Post by spikoley on 2010-12-13
Thanks for the reply.  I will start searching for it.  Below I provided the details of the Firewire device just in case somebody out there knows what I need to use.

lspci
```
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
```

Below are the details of the modules for Firewire.

lsmod | grep firewire
```
firewire_ohci          21106  0 
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core

```

---

