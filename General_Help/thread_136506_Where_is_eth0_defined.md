---
title: "Where is eth0 defined?"
date: 2006-02-26
forum: General Help
---

### Post by calutateo on 2006-02-26
Hi,

I have an Intel network card 
[INDENT]root@s168m193:~# lspci -v -s 02:01.0
0000:02:01.0 Ethernet controller: Intel Corp. 82547EI Gigabit Ethernet Controller (LOM)
        Subsystem: Unknown device 1734:101e
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
        Memory at e2000000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at 3000 [size=32]
        Capabilities: [dc] Power Management version 2
[/INDENT]
and I would like to know which module is associated with the card.
In Red Hat you will find an alias entry in /etc/modules.conf or /etc/modprobe.conf, however, I cannot find where eth0 is defined in Ubuntu.

Regards,
Carsten

---

### Post by ahave2005 on 2006-02-26
Try:

> sudo ethtool -i eth0

/ahave

---

