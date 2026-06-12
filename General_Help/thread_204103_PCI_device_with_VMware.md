---
title: "PCI device with VMware?"
date: 2006-06-26
forum: General Help
---

### Post by jinx099 on 2006-06-26
Theres a lot of talk about VMware on these forums, so I thought I'd ask you guys for help.  I want to use my PCI tv tuner card on windows over VMware on Ubuntu, which is recognized by the system, but not really working.  How can I setup VMware to use a PCI card?

---

### Post by jinx099 on 2006-06-26
bump?

---

### Post by Stormbringer on 2006-06-27
VMware (and the same goes for Parallels Workstation and such) CANNOT access the Hosts PCI devices (read: the real underlying hardware)!

You are only able to SHARE your ...

... Network,
... Serial,
... Parallel,
... USB (limited to 2 devices),
... Hard Drive,
... Floppy,

... with VMware through specialized software access mechanism - but you don't have any direct access to the underlying hardware.

Virtualization software like VMware creates it's own PC-within-PC runtime environment --- see it as a kind of Sandbox (to keep it very simple).

However, if you attach a USB-based TV-Tuner you'll be able to access it from within VMware as you can set the device to be available to VMware (see VMware Manual on this matter).

Storm.

---

