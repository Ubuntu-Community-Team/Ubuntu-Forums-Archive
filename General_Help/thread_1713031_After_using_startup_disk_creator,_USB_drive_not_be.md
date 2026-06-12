---
title: "After using startup disk creator, USB drive not being detected"
date: 2011-03-23
forum: General Help
---

### Post by kaldor on 2011-03-23
I have never made a live USB image before, so I gave it a shot. I have a 4 gb drive that I decided to install Natty daily on. I am on a fully updated Ubuntu 10.10 install.

I ran the disk creator and followed instructions as written on the Ubuntu Download page. Simple enough, I quickly did it and it finished without errors. It was mounted on my desktop as "EFI". I unmount, then remove it.

So I go to the Dell PC I was going to boot it from and try booting from USB. It said "Missing Operating System" instantly. I assumed it was just a Natty error.

So then I plug it into my HP laptop. Nothing happens. I look around and it's nowhere to be found. 

Same thing on the Mac. Not mounting, not showing up anywhere.

I rebooted into the Dell and tried plugging in the USB drive there. Again, nothing. The Dell is running Fedora 12.

Any ideas?

Edit with more info. Here's dmesg with the USB drive plugged in:

```
$ dmesg | tail -n15
[  105.689036] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  105.689042] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[  165.950502] usb 2-1: USB disconnect, address 4
[  397.020197] usb 2-1: new high speed USB device using ehci_hcd and address 5
[  397.155035] scsi6 : usb-storage 2-1:1.0
[  398.154571] scsi 6:0:0:0: Direct-Access                               0.00 PQ: 0 ANSI: 2
[  398.155851] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  398.160431] sd 6:0:0:0: [sdb] 7897088 512-byte logical blocks: (4.04 GB/3.76 GiB)
[  398.161058] sd 6:0:0:0: [sdb] Write Protect is off
[  398.161065] sd 6:0:0:0: [sdb] Mode Sense: 00 00 00 00
[  398.161070] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  398.167700] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  398.167713]  sdb: sdb1 sdb2
[  398.470847] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  398.470858] sd 6:0:0:0: [sdb] Attached SCSI removable disk

```

---

### Post by fabricator4 on 2011-03-23
> **kaldor said:**
> 
Any ideas?

Edit with more info. Here's dmesg with the USB drive plugged in:


No, it's not mounting.  What happens when you try to mount it manually?

Try another USB drive?

Chris

---

### Post by PCNetSpec on 2011-03-23
I had a USB stick do the same thing the other day... I ended up having to use gnome-disk-utility to format the stick as EXT4, then again as FAT(32), then it would mount and/or be recognised by other systems.

Used startup disk creator again, and the LiveUSB worked fine the second time.

Go figure....

---

