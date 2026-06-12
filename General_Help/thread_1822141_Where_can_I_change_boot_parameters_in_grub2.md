---
title: "Where can I change boot parameters in grub2"
date: 2011-08-10
forum: General Help
---

### Post by Midahed on 2011-08-10
OK, so I'll admit it....  I have a mental block whenever I'm confronted with anything to do with grub2.  Changing things in menu.lst was SO much simpler....

I want to include the command 'acpi=off' - but where do I put it?  Can I change the detail of an existing grub entry in this way, or do I have to create a complete custom menu entry in grub.d and include it in that?

I've tried reading the grub2 tutorials, but it hasn't really helped!

---

### Post by kvaadithya on 2011-08-10
Please try /etc/default/grub.

Open the above file (as root) in a text editor, and add acpi=off to the GRUB_CMDLINE_LINUX line. To be clear, after adding the option, your /etc/default/grub file must contain the line:

```

GRUB_CMDLINE_LINUX="acpi=off"

```

Please run "sudo update-grub" and reboot. That should solve your problem.

---

### Post by Midahed on 2011-08-10
Thanks very much for your help.  That fixed it.

---

