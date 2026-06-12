---
title: "(Oneric) Installing command line system on VMWare Fusion 4.0.2 on VMWare"
date: 2011-11-04
forum: General Help
---

### Post by pkambadu on 2011-11-04
Hey Guys,

I want to install a command line system on VMWare Fusion 4.0.2. I downloaded the latest (11.10) alternate CD, chose "Expert Mode" to get to the boot menu and typed in "cli" as instructed elsewhere on these pages. Unfortunately, I get the following error:

VFS: Cannot open root device "(null)" or unknown-block (8,1).

It then proceeds to ask me to give it "root=" option. I tried with both SCSI and IDE as my virtual disks and neither helps. I have successfully installed 11.10 on the same configuration using the regular install process (graphical).

Anju

---

### Post by pkambadu on 2011-11-04
Its fixed --- I simply had to add "cli" to the given boot line instead of deleting everything and having just "cli" on the boot line.

---

