---
title: "Memory stick seen by XP but not Ubuntu"
date: 2012-08-01
forum: General Help
---

### Post by Matt-In-The-Hat on 2012-08-01
I bought a Toshiba 32gb (I read reviews after purchase) and Windows sees it fine. Ubuntu does nothing.

lsusb adds this line:

Bus 001 Device 016: ID 0011:7788

with nothing after the ID. Gparted sits scanning all devices until I take it out. The entire system gets part way, if restarted with the stick in, and just sits with a black screen until I take the stick out (then it loads up Ubuntu happily).

fdisk -l shows hard drives then sits quietly without giving a prompt back.
df -h makes no mention of it.

syslog says:

Aug  1 22:47:26 Trotsky kernel: [264509.136059] usb 1-6: reset high speed USB device using ehci_hcd and address 16
Aug  1 22:47:26 Trotsky kernel: [264509.352331] sd 14:0:0:0: [sde] Unhandled error code
Aug  1 22:47:26 Trotsky kernel: [264509.352337] sd 14:0:0:0: [sde]  Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
Aug  1 22:47:26 Trotsky kernel: [264509.352342] sd 14:0:0:0: [sde] CDB: Read(10): 28 00 03 e7 ff f8 00 00 01 00
Aug  1 22:47:26 Trotsky kernel: [264509.352356] end_request: I/O error, dev sde, sector 65535992
Aug  1 22:47:26 Trotsky kernel: [264509.352361] Buffer I/O error on device sde, logical block 8191999
Aug  1 22:47:57 Trotsky kernel: [264540.112040] usb 1-6: reset high speed USB device using ehci_hcd and address 16

Any ideas?

Thanks,

Matthew.

---

### Post by sgoodman on 2012-08-01
are you using usb 3.0 ?

it seem to me that the usb stick is behaving in a corrupt way, maybe.

if it is a usb 3.0 port, you could try to rmmod xhci_hcd and then modprobe xhci_hcd.

this will reload the usb 3.0 driver, or activate it if it is not loaded.

what is ls /dev/sd* before  and after plugging in ?

---

### Post by Matt-In-The-Hat on 2012-08-01
USB 2.0 (computer is ~6 years old). Computer with XP is even older but has no trouble.

---

### Post by sgoodman on 2012-08-01
is the usb stick formatted to ntfs ?

also the guys at archlinux had this a while ago

[https://bbs.archlinux.org/viewtopic.php?id=129297](https://bbs.archlinux.org/viewtopic.php?id=129297)

---

### Post by Matt-In-The-Hat on 2012-08-01
Fat32 formatting. Did that on xp to try to get it to work on Ubuntu.
Files copy to and from fine on xp.

---

### Post by joco1500 on 2012-08-01
just get another usb drive

---

### Post by sgoodman on 2012-08-01
> **joco1500 said:**
> just get another usb drive

and post results

---

### Post by Matt-In-The-Hat on 2012-08-01
I've got another USB drive, plus refund for this one, but fancied trying suggestions for getting this to work.

Can the ROM of a flash drive be, erm, flashed with new drivers?

Any other ideas (apart from new drive and new computer)?

---

### Post by stoneage on 2012-08-01
Try plugging it into XP, 'remove it safely', then try it in Ubuntu.

Another suggestion is reformatting it Fat32 in Ubuntu and see if that helps.

---

