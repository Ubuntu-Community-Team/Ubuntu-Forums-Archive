---
title: "&quot;No Such Partition&quot; and &quot;GRUB Rescue&quot;"
date: 2010-11-16
forum: General Help
---

### Post by DnDer on 2010-11-16
My friend has a eee-pc, and I'd set up a dual-boot for her (ubuntu/win xp), and she told me tonight that she saw an error regarding symantec ghost. She thinks. (She does not use disk cloning software, nor probably really knows what it is.) She was prompted to reboot her computer after this message came up.

At boot she's presented with "No such partition" and "grub rescue."

Quick research tells me to NOT use grub rescue but to boot into windows recovery console. Before I have her try to use either recovery console or grub rescue, I thought I'd check in here.

---

### Post by rudeboyskunk on 2010-11-16
Your MBR is corrupted or not pointing to the grub config files on your linux partition.  I had the same problem last night, and I followed the instructions here to fix:  [http://www.hackourlives.com/restore-grub-2-0-after-windows-7-install-ubuntu-10-04-or-9-10/](http://www.hackourlives.com/restore-grub-2-0-after-windows-7-install-ubuntu-10-04-or-9-10/)

---

