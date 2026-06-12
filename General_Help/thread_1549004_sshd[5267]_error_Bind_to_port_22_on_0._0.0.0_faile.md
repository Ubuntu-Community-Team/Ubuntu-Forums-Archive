---
title: "sshd[5267]: error: Bind to port 22 on 0. 0.0.0 failed: Address already in use."
date: 2010-08-09
forum: General Help
---

### Post by Jay89 on 2010-08-09
Hey guys,
      I am currently working with a ubuntu server version 2.6.24-19. This is the backup server for the system, up until recently it has been functioning fine with no problems. But we noticed in /var/log that most of the backups start and stop at the exact same time or 1 minute or so later. (example: "server1" backup started at 2:05 and ended at 2:05) which obviously means that they are not backing up because they are big servers with gigs of data. 

      I also noticed a few other errors and are having difficulty finding out what thy mean and how to fix them.

      One is [B]"sshd[5267]: error: Bind to port 22 on 0. 0.0.0 failed: Address already in use. "
       [/B]And the other is [B]"kernel: [   33.530258] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found. "

[/B]Repeated over and over.

If someone could please help it would be greatly appreciated.

Thank you!!


PS. The command we use to pull the data from the servers is **rsync**.

---

