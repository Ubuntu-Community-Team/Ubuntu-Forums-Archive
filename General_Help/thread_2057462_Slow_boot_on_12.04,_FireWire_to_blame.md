---
title: "Slow boot on 12.04, FireWire to blame?"
date: 2012-09-13
forum: General Help
---

### Post by El Zoido on 2012-09-13
Hello!

First thing: No it's not FireWire, I just assumed so at first, see below why.
Still could use some help, though. ;)
Since 11.10 or such, I suffer from rather slow boot times in Ubuntu.
My system is:

AMD Phenom II X4 965 @3.6 GHz
GigaByte GA870A-UD3 Mainboard
NVidia GTX460 1GB
8 GB of Ram

Up to 11.04 Ubuntu used to boot in 20-30 seconds, but since 11.10 (and now on 12.04), boot times are much longer. Right now it's about 1 minute.
Today I decided to check again if something can be done and had a look at the output of dmesg, which contained this:

```

...
[    3.871544] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    3.871546] EXT4-fs (sda5): write access will be enabled during recovery
[    3.896089] firewire_ohci: Added fw-ohci device 0000:04:0e.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    4.066369] EXT4-fs (sda5): recovery complete
[    4.066589] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    4.396130] firewire_core: created device fw0: GUID 00157dc7001c6f65, S400
[   33.792044] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   33.792047] ata2.00: failed command: IDENTIFY PACKET DEVICE
[   33.792051] ata2.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[   33.792051]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   33.792053] ata2.00: status: { DRDY }
[   33.792056] ata2: hard resetting link
[   34.284058] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   35.086564] ata2.00: configured for PIO4
...
```

So between 4.39 and 33.79, the boot practically stopped. At first I thought it's due to Firewire, because:
I blacklisted everything in blacklist-firewire.conf and it booted in less than 30 seconds, yielding:

```
[    3.334309] usbcore: registered new interface driver usbhid
[    3.334310] usbhid: USB HID core driver
[    3.809310] firewire_ohci 0000:04:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.864113] firewire_ohci: Added fw-ohci device 0000:04:0e.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    3.874657] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    3.874659] EXT4-fs (sda5): write access will be enabled during recovery
[    4.364132] firewire_core: created device fw0: GUID 00157dc7001c6f65, S400
[    4.920902] EXT4-fs (sda5): recovery complete
[    4.921123] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   13.798798] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

So the long wait seems gone (although it still hangs on eth0? well, still much better)
On reboot, however, it hangs again, with the same output as in the first section.

So what's going on?

---

### Post by El Zoido on 2012-09-14
*bump* :oops:

---

### Post by Bucky Ball on 2012-09-14
Are you upgrading or doing clean installs each time?

---

### Post by El Zoido on 2012-09-14
Clean install.
Although I'm not sure if I deleted all invisible folders on my (separate) home partition when I last installed it.
Then again, I doubt that any stuff there will affect the boot process that early.

---

