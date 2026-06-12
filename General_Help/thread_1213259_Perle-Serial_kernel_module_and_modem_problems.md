---
title: "Perle-Serial kernel module and modem problems"
date: 2009-07-14
forum: General Help
---

### Post by mpetty423 on 2009-07-14
I havea multi-port PCI-RAS Multi-Modem card from Perle.

They supply open source drivers for their card, which are available from their site, and from their install CD.

I downloaded the source tar from their site, and installed it.  It built everything, and initialized the kernel module.  Sweet.

both dmesg, and /var/log/syslog show:

```
[  415.278652] Perle Serial driver version 3.6.10 (2009-02-06) with SHARE_IRQ SERIAL_PCI enabled

```I don't see any errors wherever I look, but the serial ports/modem never show up.  Where would I check to see if any of these ports are created?  The documentation says that they should be installed at /dev/ttyPS0-7, but everything that I use to query those ports shows nothing there.

Anyone have any idea what I may be doing wrong?

---

