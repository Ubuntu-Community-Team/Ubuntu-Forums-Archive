---
title: "Ubuntu 10.10 and Sata III"
date: 2010-11-24
forum: General Help
---

### Post by xplosivo on 2010-11-24
Just a quick question about compatibility. For some reason when trying to install Ubuntu 10.10, it will not recognise my hard drive. The only thing I can think of is maybe 10.10 is not compatible with Sata III; I have a Sata III hard drive plugged into a Sata III port and Ubuntu does not see it at all. Just wondering if this is a known issue or not. Or if someone else has an idea of what might be the issue I'd be glad to hear it.

Thanks

---

### Post by xplosivo on 2010-11-25
No one knows? Has anyone installed this version of Ubuntu on a Sata III drive? Even that would let me know if this is the issue or not.

---

### Post by OrangeShoes on 2010-12-16
I have had no issue installing Ubuntu 10.04 on a system with a WD Black Edition 1TB 6Gb/sec hard drive and a MSI 870A-G54 motherboard. I was careful to use SATA III cables on the build - not SATA II cables. Make sure you've enabled AHCI in the BIOS before you install Ubuntu. Ubuntu needs AHCI enabled for the Sata III controller in order to correctly identify the disks on it. AHCI, or Advanced Host Controller Interface.

---

