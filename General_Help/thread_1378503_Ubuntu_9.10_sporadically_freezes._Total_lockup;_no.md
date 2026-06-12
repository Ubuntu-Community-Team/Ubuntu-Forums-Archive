---
title: "Ubuntu 9.10 sporadically freezes. Total lockup; no clear cause."
date: 2010-01-11
forum: General Help
---

### Post by polemicist on 2010-01-11
Hello. I migrated over from debian, keeping my /home/ directory, which was on a separate partition. At varying intervals after boot (5 minutes to 5 hours) Ubuntu will completely freeze, seemingly without cause. I'm forced to go through with Alt+Sys+REISUB because the machine simply won't respond.

I'm unsure what information will help. Here's a copy of the output from lspci:

```

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI
01:01.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)

```

I'll post anything else; just request it.

---

### Post by jordilin on 2010-01-11
Could you paste the lines of /var/log/messages at the time that happens?

---

### Post by polemicist on 2010-01-11
> Could you paste the lines of /var/log/messages at the time that happens?

Sure.

```

Jan 11 20:01:55 davidubuntu kernel: [  287.020443] ata2.01: configured for UDMA/33
Jan 11 20:01:55 davidubuntu kernel: [  287.020913] ata2: EH complete
Jan 11 20:02:55 davidubuntu kernel: [  347.300081] ata2.01: limiting speed to UDMA/25:PIO4
Jan 11 20:03:00 davidubuntu kernel: [  352.352039] ata2: link is slow to respond, please be patient (ready=0)
Jan 11 20:03:05 davidubuntu kernel: [  357.329206] ata2: device not ready (errno=-16), forcing hardreset
Jan 11 20:03:05 davidubuntu kernel: [  357.329220] ata2: soft resetting link
Jan 11 20:03:05 davidubuntu kernel: [  357.488562] ata2.00: configured for UDMA/33
Jan 11 20:03:05 davidubuntu kernel: [  357.496982] ata2.01: configured for UDMA/25
Jan 11 20:03:05 davidubuntu kernel: [  357.500083] ata2: EH complete
Jan 11 20:08:15 davidubuntu pulseaudio[1494]: ratelimit.c: 2 events suppressed

```

---

### Post by jordilin on 2010-01-11
Doesn't say that much, but I see a bug in [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/368941](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/368941) about that pulseaudio trace. Freezes could happen due to the X servers, faulty hard drives, etc... 
You say you are keeping home partition from a debian installation, are the permissions over there set up correctly?

---

### Post by polemicist on 2010-01-11
I assume so... that is, david can do anything to /home/david/.

---

### Post by warfacegod on 2010-01-11
I'm wondering if this is a hardware issue. Over heating CPU, corrupted RAM, etc. Maybe time to run memtest from grub menu and clean the heatsink on the processor.

---

### Post by polemicist on 2010-01-11
I'll give it a go. This computer is fairly old, and I confess to dusting it more seldom than I ought.

---

### Post by warfacegod on 2010-01-11
If you remove the heat sink, reapply thermal grease to it.

---

