---
title: "GRUB2 Dynamic Defauls"
date: 2012-01-10
forum: General Help
---

### Post by ElvisTheKing on 2012-01-10
I'm building a system that uses Ubuntu as the native OS that boots via Virtua Box a windows 7 partition (using hardware profiles), unfortunately when booting the VM it throws up the GRUB2 boot loader, selecting the windows partion works fine but by default it selects the Ubuntu partition to load (i.e. the host OS), as you can imagine trying to boot this partion causes "Bad Things(tm)" to happen, even with no timeout on the boot menu it's a little too easy to select it by accident.

Is there anyway to get GRUB2 (via a similar hardware profiles type method) to default to Ubuntu if booting the "real" machine or Windows 7 if booting the VM?

A work around is obviously to set the default to be the Windows 7 but a GRUB2 solution would probably be more "elegant".

Cheers

---

