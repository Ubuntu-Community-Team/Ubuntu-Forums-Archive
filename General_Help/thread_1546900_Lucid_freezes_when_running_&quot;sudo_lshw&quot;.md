---
title: "Lucid freezes when running &quot;sudo lshw&quot;"
date: 2010-08-06
forum: General Help
---

### Post by Benj_C on 2010-08-06
Hi,

I can run "lshw" without any problem. But when running it in superuser mode, the system freezes and requires a hard reboot. 

I'm certain that it was running fine on Karmic. I can't remember running this on Lucid before. So it's related to either Lucid or a new update.

The system seems to freeze when running the PCI test or SCSI test. I tried to disable either one of them, without any success. And I couldn't find much information in the log files.

I hope somebody will be able to help. I couldn't find anything online.

Best,

Ben

---

### Post by useResa on 2010-08-24
I experienced the same and found that there is a confirmed bug about this issue.

See [bug #614008]("https://bugs.launchpad.net/ubuntu/+source/lshw/+bug/614008")

---

