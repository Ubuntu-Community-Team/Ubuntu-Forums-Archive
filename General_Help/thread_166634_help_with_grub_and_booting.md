---
title: "help with grub and booting"
date: 2006-04-26
forum: General Help
---

### Post by scpike on 2006-04-26
I had windows XP installed on the master hda drive, Fedora core 4 installed on a second hard drive, and Vista installed on a third hard drive.  Vista's bootloader currently loads XP's loader, which then either loads fedora or windows xp.  Grub was never installed over either of thse loaders.

Today I installed Ubuntu on the same partition as fedora, and overwrote the partition which fedora had installed grub on with ubuntu's grub during the install process, leaving the mbr intact. But now when I try to load the entry in XP's loader that was fedora, I get a command line prompt:

grub>

and nothing from there.

how do I set up grub on this partition so that it allows me to choose either ubuntu or fedora to bood when it is called?

thanks

---

