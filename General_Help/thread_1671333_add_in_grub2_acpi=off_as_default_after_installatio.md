---
title: "add in grub2 acpi=off as default after installation?"
date: 2011-01-19
forum: General Help
---

### Post by gypsumwolf on 2011-01-19
how do I add in grub2 acpi=off as default boot option?

What line do I add to /etc/grub.d/40_custom ?

---

### Post by kerry_s on 2011-01-19
gksudo gedit /etc/default/grub

change:
[B]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[/B]to
[B]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
[/B]

run "sudo update-grub" in the terminal.

---

