---
title: "Access to /proc/config.gz"
date: 2011-01-22
forum: General Help
---

### Post by wilsonsamm on 2011-01-22
How can I get access to that file? I want to start tweaking my kernel with the current configuration as a starting point.

---

### Post by kidders on 2011-01-23
Hi there,

The /proc interface to the kernel configuration is not enabled in Ubuntu by default. Presumably the idea was not to bloat the kernel unnecessarily. It tends to be copied into /boot though, so **cat /boot/config-`uname -r`** should accurately reflect your kernel's configuration (unless you've altered/deleted it for some reason).

[COLOR="DimGray"]Do take care when modifying your kernel. You can quite easily break installed software/damage your hardware/make your system unbootable/etc.[/COLOR]

---

