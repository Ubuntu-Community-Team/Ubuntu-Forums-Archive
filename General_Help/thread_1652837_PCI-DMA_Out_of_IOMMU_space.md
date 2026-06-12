---
title: "PCI-DMA: Out of IOMMU space"
date: 2010-12-25
forum: General Help
---

### Post by Kranjak on 2010-12-25
Hi guys,
yesterday I've upgrade my hardware configuration up to 4GB of RAM. Today I've found some problems with my Ubuntu 10.10, like music stops playing or file system that became read-only. I've found this errors messages running dmesg:

```
PCI-DMA: Out of IOMMU space for xxx bytes
```I've tried to add "iommu=memaper=3" and "iommu=noaperture" to boot options as found with google, but problem still remains. Some ideas?

Tnx

---

### Post by dcstar on 2010-12-25
> **Kranjak said:**
> Hi guys,
yesterday I've upgrade my hardware configuration up to 4GB of RAM. Today I've found some problems with my Ubuntu 10.10, like music stops playing or file system that became read-only. I've found this errors messages running dmesg:

```
PCI-DMA: Out of IOMMU space for xxx bytes
```I've tried to add "iommu=memaper=3" and "iommu=noaperture" to boot options as found with google, but problem still remains. Some ideas?

Tnx

Check advanced BIOS settings so **everything** is mapped below 4GB. Otherwise the RAM may be incompatible.

---

### Post by Kranjak on 2010-12-26
> **dcstar said:**
> Check advanced BIOS settings so **everything** is mapped below 4GB. Otherwise the RAM may be incompatible.

for example? what should I look?
I've worked for a day without problems, with several reboots and it worked fine, it seems strange to be a RAM incompatibility.

---

### Post by Kranjak on 2010-12-28
I've tried with an lspci for find device that does errors.
I've found this was a problem regarding my second ethernet card. Removing this has resolved my problem.

---

