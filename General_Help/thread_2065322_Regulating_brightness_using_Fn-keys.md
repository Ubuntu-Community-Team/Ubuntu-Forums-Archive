---
title: "Regulating brightness using Fn-keys"
date: 2012-10-01
forum: General Help
---

### Post by richter12 on 2012-10-01
Hello,
i have a laptop with the newest Ubuntu-version (12.04). I want to use the FN-Keys to adjust the brightness of my screen, but it doesnt work. Normally it should be FN+left arrow/right arrow. However adjusting the volume with FN+ up arrow/down arrow works fine.

I already searched for a few soulutions, for example tried to replace in the Grub-File 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```with

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
```or
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash cpi_osi=Linux"
```but it all doesnt work for my laptop. How can I fix this problem?

Thank you very much!

Richter

---

