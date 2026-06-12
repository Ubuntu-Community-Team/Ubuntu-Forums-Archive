---
title: "Ubuntu 9.10 server won't start after update"
date: 2010-01-27
forum: General Help
---

### Post by climhazzard on 2010-01-27
Hi all,

I recently installed 9.10 server (64 bit) on a machine at work.  Everything was working well until I logged in this morning and a message appeared saying the system needed to be rebooted.  I figured this is from a software update, so I rebooted it and now I'm stuck.  Here's what appears on the screen:

fsck from util-linux-ng 2.16
/dev/md0: clean 57906/122214272 files, 1083173/48827520 blocks (check after next mount)
fsck from util-linux ng 2.16
[    5.932276] ACPI: I/0 resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[    5.978889] shpchp 000:00:01.0: Cannot reserve MMIO region
/dev/md1: clean, 11/7020544 files, 488647/28075568 blocks
* Reloading /etc/samba/smb.conf smbd only
* could not access PID file for nmbd

After this happens I cannot do anything, I've also tried recovery mode with no luck.  Any help is much appreciated!

---

