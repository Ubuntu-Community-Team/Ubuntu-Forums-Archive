---
title: "Place Windows at the top of GRUB menu."
date: 2010-08-19
forum: General Help
---

### Post by Renée Jade on 2010-08-19
Hey guys,

At the moment my GRUB 2 boot menu has all the Linux kernels, then memtests, then Windows. I want it to have Windows, then Linux, then memtests. I'm thinking I can do this by renaming /etc/grub.d/10_linux, 20_memtest86+ and 30_os-prober to 20_linux, 30_memtest86+ and 10_os-prober respectively.

Does anyone know if doing this will cause disaster?

Thanks heaps.

---

### Post by Renée Jade on 2010-08-19
To add to that, /etc/grub.d/README says

All executable files in this directory are processed in shell expansion order.

  00_*: Reserved for 00_header.
  10_*: Native boot entries.
  20_*: Third party apps (e.g. memtest86+).

The number namespace in-between is configurable by system installer and/or
administrator.  For example, you can add an entry to boot another OS as
01_otheros, 11_otheros, etc, depending on the position you want it to occupy in
the menu; and then adjust the default setting via /etc/default/grub.

So if I change 30_os-prober to 09_os-prober, will it be ok?

---

### Post by Renée Jade on 2010-08-19
> **Renée Jade said:**
> 
So if I change 30_os-prober to 09_os-prober, will it be ok?

This worked perfectly.

---

