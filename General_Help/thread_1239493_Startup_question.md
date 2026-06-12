---
title: "Startup question"
date: 2009-08-13
forum: General Help
---

### Post by LuckyDucky7 on 2009-08-13
When Kubuntu starts, before the graphical loading screen, it says something about an ACPI error: expecting a [reference] type package, found type 0.
It also gives a few more error messages that flash by too fast to read- "please complain to your hardware vendor?"
It then proceeds with the normal booting process.

Is there any way to fix this? Does grub (or Kubuntu) log its bootup problems so I can at least figure out what this message says?
Could this be why the standby and hibernate functions "crash" the computer?
Any ideas?

I am using an ASUS M2N32-SLI board.

---

### Post by doas777 on 2009-08-13
I get the same error on a ubuntu box with a simlliar mobo. never caused a problem thus far.

you can access your boot log by entering into a terminal:
```
dmesg > ~/dmesg.txt
```
the output will be long, so I usually redirect it to a text file, like above. 
you can also find info in the System -> Administration -> Log File Viewer, in the syslog, message log, and xorg.0.log.

---

### Post by LuckyDucky7 on 2009-08-13
Hmm.  I think this is what shows.

[1.291432] ACPI: Expecting a [Reference] package element, found type 0

[10.742717] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.

[10.742793] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.

---

