---
title: "iSCSI login, but no device nodes?"
date: 2010-08-17
forum: General Help
---

### Post by agshekeloh on 2010-08-17
Hi,

I'm running 10.04 64-bit diskless on ESXi, installed as a minimal virtual machine.  I want this server to access an iSCSI drive.  The machine can view the iSCSI shares with iscsiadm, and can even log into the drive.  When I do an iSCSI login, this appears in /var/log/messages:

Aug 17 11:08:21 ubuntutest kernel: [1123295.329972] scsi4 : iSCSI Initiator over TCP/IP

So, it appears that open-iSCSI is working correctly.

But no new /dev/sd* nodes appear, and nothing new appears in /dev/disk/by-path.  I'd expect to see /dev/disk/by-path/ip-XXXXXXXXX.  fdisk -l shows nothing but the boot drive.  My guess is that the "minimal kernel" doesn't include some necessary module or driver.

Any suggestions on where to look, folks?

Thanks,
==ml

---

### Post by dballanc on 2010-09-01
I'm new to ISCI, but ran into the same symptoms (login ok, no device node).  In my case it was a problem on the target server.  The target device wasn't available (it was an lvm volume, with lvm stopped).

---

