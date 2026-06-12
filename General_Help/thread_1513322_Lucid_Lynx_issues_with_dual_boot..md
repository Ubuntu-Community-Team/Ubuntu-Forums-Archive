---
title: "Lucid Lynx issues with dual boot."
date: 2010-06-19
forum: General Help
---

### Post by gypaete09 on 2010-06-19
[QUOTE=bcbc;9220840]A lot of users are overwriting their windows boot sector due to a confusing message with the grub2 install. It says something like 'Choose where to install grub. If you are not sure select all partitions'. And this leads some to select their windows partition.

Yes, it happened to me, my (two) windows partitions had a problem, but booting from the (XP in this case) install disk and running FIXBOOT C:
fixes the problem.

Not so on my newly acquired laptop with Vista:
After successful install of Lucid and a few days of working under Lucid, I found that Vista would not boot anymore (hadn't tried since lucid install), but Vista would trigger the system restore utility on the system restore partition, and worse: It would be possible to 
restore to the (reduced size)  Windows partition, but system restore would
restart, unless I'd give Vista the whole disk back.

A local computer shop here confirmed they had heard of that "fightback" symptom, as I'd call it.
On my laptop, I simply decided to shoot the restore partition and Vista altogether and go Lucid-only, plus Virtualbox and XP for the odd I-must-run-Windoze cases, and with the improved USB support, everything is fine.

Please, has anyone seen the same behaviour of Vista restoration? I use a Acer Emachines 625 (2Gb RAM) for Lucid, and it races under Lucid AMD64 while it crawls under Vista.

:p

---

### Post by philinux on 2010-06-19
Moved out of sticky to own thread.

---

