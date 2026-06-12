---
title: "USB Flash Drive causes soft lockup"
date: 2012-09-03
forum: General Help
---

### Post by brpylko on 2012-09-03
When I plug in a USB Flash Drive, my computer begins to operate very slowly and eventually freeze completely. dmesg | tail says that there was a soft lockup. This problem only applies to things that Ubuntu thinks are flash drives, as plugging in my phone or an iPhone works. Somewhere, someone said that adding acpi=off to the grub configuration would fix it, and it did, but also broke my wireless (plus it's a pain not to have acpi). I am looking for a solution that will not break anything else.

System specs:
Ubuntu 12.04 amd64 (kernel 3.2)
AMD E-300 APU
Toshiba Satellite c655d-s5535

This is the output of dmesg | tail right before the soft lockup:

[ 1066.526825] scsi 4:0:0:0: Direct-Access     SanDisk  Cruzer Glide     1.26 PQ: 0 ANSI: 5
[ 1067.005743] psmouse serio1: Touchpad at isa0060/serio1/input0 lost synchronization, throwing 5 bytes away.
[ 1067.307708] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 1067.314726] sd 4:0:0:0: [sdb] 7821312 512-byte logical blocks: (4.00 GB/3.72 GiB)
[ 1067.571743] sd 4:0:0:0: [sdb] Write Protect is off
[ 1067.571755] sd 4:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 1068.597617] psmouse serio1: resync failed, issuing reconnect request
[ 1069.109956] usb 1-1: USB disconnect, device number 3
[ 1072.700134] sd 4:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 1072.700924] sd 4:0:0:0: [sdb] Attached SCSI removable disk

---

### Post by cprofitt on 2012-11-09
Did this go away when you upgraded to 12.10?

What is the file system on the USB drives in question?

---

### Post by brpylko on 2012-11-09
Sorry, I completely forgot about this thread, I'll change it to solved. Here's what I've learned:
* Upgrading to 12.10 (and kernel 3.5) fixed the problem
* FS does not matter, it caused a soft lockup whether it was FAT, ext4, iso9660, or no file system (dd'd /dev/zero to it on another computer).
* It seems to be a problem with usbmodeswitch, as temporarily uninstalling that package fixed it, and it continued to work after reinstallation until I rebooted (possible a kernel module not being activated?)

---

