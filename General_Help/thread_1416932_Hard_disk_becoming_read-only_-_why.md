---
title: "Hard disk becoming read-only - why?"
date: 2010-02-26
forum: General Help
---

### Post by StuartN on 2010-02-26
I have just freshly installed Karmic on hardware that was previously running Intrepid without any problems. I have not installed anything beyond a few bog-standard applications.

I am now running into regular system lock-ups because the / partition is becoming read-only. Once this happens I am unable to start any application or to shut down, because there is no write access.

If I happen to have a terminal open, then it is apparent that the disk has become read-only because I can not remove, create or modify any file. If I do not have a terminal open, then I can not open one.

Obviously there is nothing written to any log.

Does anyone have any suggestions to fix this?

---

### Post by rnerwein on 2010-02-26
hi
the only reason i know that a filesystem becomes remounted "ro" is that when there are problems with the disk - mostely hardware errors ( see in your /etc/fstab for / mount options ). but normaly there must be a log in any logfile in /var/log. on the other side the message buff couldn't be flushed.
there for try in a terminal: dmesg | more.
good luck

ciao

---

### Post by StuartN on 2010-02-27
> **rnerwein said:**
> the only reason i know that a filesystem becomes remounted "ro" is that when there are problems with the disk

I think that it is more likely a software issue introduced by the install of Karmic than a hardware issue. I have found a lot of related threads, but none with a solution so far.

> **rnerwein said:**
> on the other side the message buff couldn't be flushed.
there for try in a terminal: dmesg | more.

I will keep a terminal open for the next time this happens. Hopefully I will find something and not have to reinstall Hardy.

Actually there is some oddness in Karmic's handling of the hard disk drive - this is from dmesg just after resume from standby:

```
[ 2849.920538] sd 0:0:0:0: [sda] Starting disk
[ 2850.036576] ata5.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[ 2850.036580] ata5.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
[ 2850.052519] ata5.00: configured for UDMA/33
[ 2850.060039] ata3: SATA link down (SStatus 0 SControl 300)
[ 2850.060069] ata2: SATA link down (SStatus 0 SControl 300)
[ 2850.060121] ata4: SATA link down (SStatus 0 SControl 300)
[ 2850.224020] ata1: softreset failed (device not ready)
[ 2850.224024] ata1: applying SB600 PMP SRST workaround and retrying
[ 2850.388031] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 2850.436599] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[ 2850.437418] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[ 2850.437420] ata1.00: configured for UDMA/133
[ 2850.460119] PM: resume devices took 1.096 seconds
[ 2850.460187] PM: Finishing wakeup.
```

I don't know what these messages mean, but I guess that some ACPI or other startup option might handle the disk properly?

---

