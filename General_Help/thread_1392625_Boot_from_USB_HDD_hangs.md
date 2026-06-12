---
title: "Boot from USB HDD hangs"
date: 2010-01-28
forum: General Help
---

### Post by milton1 on 2010-01-28
This is more of a minor irritation than serious problem, but I would love to know if there is a fix.

I have kubuntu 9.10 installed on a USB hard drive, with separate partitions for "/boot" "/" and "/home". On booting the machine, grub throws an error that it can't find a drive. The UUID it throws is the root partition. It then waits a few seconds and proceeds to boot from the partition is just said it can not find. The boot process hangs for four to five minutes, then proceeds without any more problems. This has happened on two completely different machines (though with different amounts of hang time).

Any ideas on what the issue is, or how I might fix it?

The external drive is a Seagate FreeAgent. I am using grub2. The computer it is being regularly used on is a Gateway E-series, P4, 768 MB RAM.

---

### Post by milton1 on 2010-02-24
Update: This is definitely a hardware / BIOS issue. Plugged into my newer laptop, the problem does not exist.

---

