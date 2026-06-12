---
title: "Ridiculously slow file transfer"
date: 2011-03-19
forum: General Help
---

### Post by The_Eggert on 2011-03-19
Hello :)
For the past week+ I have been experiencing very slow file transfers, moving files from one HDD to another - both internal, connected with SATA, should anyone care..
When I move any file, regardless of its size, it is moved with 1.1 MB/sec at very best :(
That's a major pain in the behind, even for moving small amounts of data!

If anyone could point me in the right direction, or give me a solution, it would be greatly appreciated :)
Do tell what information you need ;)

---

### Post by The_Eggert on 2011-03-19
It would appear the problem isn't there, when moving files to a USB flash drive - Formatted NTFS..

---

### Post by The_Eggert on 2011-03-21
Bump..

---

### Post by antaios256 on 2011-03-21
what are the 2 file systems your transferring between, are they both ext4, fat 32, ?

---

### Post by The_Eggert on 2011-03-22
> **antaios256 said:**
> what are the 2 file systems your transferring between, are they both ext4, fat 32, ?

They are both ext4 :)
One being the root system

---

### Post by coldraven on 2011-03-22
Check that your SATA cables are fully inserted, they may have got loose.

---

### Post by antaios256 on 2011-03-22
well with them both being ext4 I'm not sure what the problem might be. I've done some research and there was a problem copying large files. causing slowdowns of the entire OS but i cant see anything directly related to your issue. sorry i cant be of more help.

---

### Post by The_Eggert on 2011-03-24
> **coldraven said:**
> Check that your SATA cables are fully inserted, they may have got loose.
Just checked and double checked that, and they didn't seem loose, nor did it fix the problem - But thanks nonetheless :)

> **antaios256 said:**
> well with them both being ext4 I'm not sure what the problem might be. I've done some research and there was a problem copying large files. causing slowdowns of the entire OS but i cant see anything directly related to your issue. sorry i cant be of more help.
If nothing else it at least tells me, that it's not just my system using all its resources on file transfers - At least used to.. :)

---

### Post by tgalati4 on 2011-03-24
Do a file transfer.  While waiting:

Open a terminal:

dmesg | tail -50

Any disk-related messages?

I had similar thing happen to me on Dapper Drake machine that had been up for several years--continuously.  I was getting read errors and IO waits in the dmesg.  Great, failing hard disk.

Opened up the machine.  The power connector to the drive had vibrated loose (after several years) and the drive was literally going to sleep without power.  The kernel said, "I'll just wait here until the data comes back."

---

### Post by The_Eggert on 2011-03-25
> **tgalati4 said:**
> Do a file transfer.  While waiting:

Open a terminal:

dmesg | tail -50

Any disk-related messages?


As far as I can tell, it doesn't say anything like IO-error or the like..But then again, I'm not sure what to look for :P
It does however mention something about some error and remount..? :)
And by the way, the two discs are sda1 and sdb1..

Here's the output of 'dmesg | tail -50'
```
[   13.617589] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   13.617590] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   13.637285] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   13.665035] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.766584] hda_codec: ALC888: BIOS auto-probing.
[   13.766587] hda_codec: ALC888: SKU not ready 0x411111f0
[   13.775863] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   13.775950]   alloc irq_desc for 45 on node 0
[   13.775952]   alloc kstat_irqs on node 0
[   13.775961] HDA Intel 0000:01:00.1: irq 45 for MSI/MSI-X
[   13.775981] HDA Intel 0000:01:00.1: setting latency timer to 64
[   14.060612] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr
[   14.724757] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   14.784613] type=1400 audit(1301055542.348:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1297 comm="apparmor_parser"
[   14.784880] type=1400 audit(1301055542.348:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1297 comm="apparmor_parser"
[   14.799389] type=1400 audit(1301055542.358:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1385 comm="apparmor_parser"
[   14.799553] type=1400 audit(1301055542.358:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1386 comm="apparmor_parser"
[   14.799766] type=1400 audit(1301055542.358:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1386 comm="apparmor_parser"
[   14.799884] type=1400 audit(1301055542.358:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1386 comm="apparmor_parser"
[   14.800228] type=1400 audit(1301055542.358:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=1389 comm="apparmor_parser"
[   14.813861] r8169 0000:02:00.0: eth0: link up
[   14.813871] r8169 0000:02:00.0: eth0: link up
[   14.927871] ppdev: user-space parallel port driver
[   15.084899] kvm: Nested Virtualization enabled
[   15.084903] kvm: Nested Paging enabled
[   15.544476]   alloc irq_desc for 46 on node 0
[   15.544479]   alloc kstat_irqs on node 0
[   15.544488] fglrx_pci 0000:01:00.0: irq 46 for MSI/MSI-X
[   15.545002] [fglrx] Firegl kernel thread PID: 1683
[   15.545218] [fglrx] IRQ 46 Enabled
[   15.797569] Bluetooth: L2CAP ver 2.14
[   15.797572] Bluetooth: L2CAP socket layer initialized
[   15.800838] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.800839] Bluetooth: BNEP filters: protocol multicast
[   15.803762] Bluetooth: SCO (Voice Link) ver 0.6
[   15.803764] Bluetooth: SCO socket layer initialized
[   15.882153] [fglrx] Gart USWC size:1280 M.
[   15.882157] [fglrx] Gart cacheable size:508 M.
[   15.882160] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   15.882162] [fglrx] Reserved FB block: Unshared offset:f8fd000, size:403000 
[   15.882164] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
[   15.925025] Bluetooth: RFCOMM TTY layer initialized
[   15.925031] Bluetooth: RFCOMM socket layer initialized
[   15.925032] Bluetooth: RFCOMM ver 1.11
[   19.703235] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   21.666903] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   21.669346] EXT4-fs (sdb1): re-mounted. Opts: commit=0
[   25.000020] eth0: no IPv6 routers present
[   56.626857] lo: Disabled Privacy Extensions
[ 1905.796375] lo: Disabled Privacy Extensions

```

---

### Post by The_Eggert on 2011-03-30
Any ideas, anyone? :)

---

### Post by The_Eggert on 2011-03-31
Due to some other problems on my computer (due to me ******* up :P) I'm going to format my computer, and install another distribution (for the fun of it..) - Hopefully that will fiz whatever the problem is :)

---

### Post by rugbert on 2012-05-19
Did reformatting fix the issue? Ive noticed that since I upgraded to 12.04 my transfer speeds are also only 1.1mps between two internal sata drives.

---

### Post by The_Eggert on 2012-05-19
> **rugbert said:**
> Did reformatting fix the issue? Ive noticed that since I upgraded to 12.04 my transfer speeds are also only 1.1mps between two internal sata drives.

Honestly, I can't remember :)
But seeing as I havn't asked around anymore since then, I would say that it might have :)
But don't go formatting, just from my "hunch" :)

---

