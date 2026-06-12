---
title: "USB flash drive issues under 9.04"
date: 2009-07-29
forum: General Help
---

### Post by dal on 2009-07-29
Hey all, having problems since upgrading my desktop ubuntu installation to 9.04 - the usb flash drive/mp3 player that used to be detected and automounted now appears to be neither. dmesg shows the usual messages :

[182425.756037] usb 1-2: new high speed USB device using ehci_hcd and address 4
[182425.890486] usb 1-2: configuration #1 chosen from 1 choice
[182425.890797] scsi16 : SCSI emulation for USB Mass Storage devices
[182425.890874] usb-storage: device found at 4
[182425.890876] usb-storage: waiting for device to settle before scanning
[182430.888484] usb-storage: device scan complete
[182430.888963] scsi 16:0:0:0: Direct-Access              Audio PlayerPQ: 0 ANSI: 0 CCS
[182430.889959] sd 16:0:0:0: [sde] 2039296 512-byte hardware sectors: (1.04 GB/995 MiB)
[182430.890453] sd 16:0:0:0: [sde] Write Protect is off
[182430.890455] sd 16:0:0:0: [sde] Mode Sense: 03 00 00 00
[182430.890457] sd 16:0:0:0: [sde] Assuming drive cache: write through
[182430.892210] sd 16:0:0:0: [sde] 2039296 512-byte hardware sectors: (1.04 GB/995 MiB)
[182430.892697] sd 16:0:0:0: [sde] Write Protect is off
[182430.892699] sd 16:0:0:0: [sde] Mode Sense: 03 00 00 00
[182430.892701] sd 16:0:0:0: [sde] Assuming drive cache: write through
[182430.892704]  sde: sde1
[182430.893905] sd 16:0:0:0: [sde] Attached SCSI removable disk
[182430.893967] sd 16:0:0:0: Attached scsi generic sg5 type 0

but then when I try 'mount /dev/sde1 /media/sde' I get told that /dev/sde1 does not exist. Similar result when I try fdisk /dev/sde.

The device does not show up in lsusb either. It does work fine on my XP laptop.

Anyone hit a similar problem to this?

---

### Post by enz1m3 on 2009-07-30
After you plug it in, can you see it in gparted?

---

### Post by dal on 2009-07-30
Nope. Gparted uses fdisk for its backend, doesn't it?

It does throw an error on stdout saying "Could not stat /dev/sde - No such file or directory"

Also, not sure if this is pertinent or not, but the drives that I do have are sda, sdb and sdc - the usb backend appears to be skipping over sdd to label my flash drive sde instead.

---

### Post by enz1m3 on 2009-08-07
Well, I can't see what's wrong there, but it if doesn't show on gparted it's not being well recognised.

Does it work on any other pc (windows, ubuntu, other linux distro)? Or you haven't tried it yet?

Do this and put the result here:

$ ls -ltra /dev/ | grep 'sdd'
$ ls -ltra /dev/ | grep 'sde'

---

### Post by ouker on 2009-08-07
[SIZE=5]You can use 'sudo mount /dev/sde1 /media/sde' have a try,but you must make sure that /media/sde is exist[/SIZE]

---

### Post by martinbaselier on 2009-08-07
It's quite strange that you don't see the device when you run lsusb. It shows up in dmesg. 

Just to get a more complete picture. What is the output of **lsusb** and **sudo fdisk -l**? You might try **sudo lsusb** too. If that output is different, please post it too.

---

### Post by dal on 2009-09-09
Sorry it took me so long to get back to the thread. There were no /dev/sde* files, even though the dmesg output lead me to believe there should be. sudo lsusb gave the same output as lsusb running as an unprivileged user, and it did work fine on my XP laptop.

It has since started working again, and as far as I can work out, if I let the battery drain completely then plug it in to my ubuntu desktop, I get the symptoms I described, although the display of the device becomes active and the battery starts recharging (connecting the device to a powered usb port is the only way to recharge it). If I let it charge for a while and then remove it and plug it back in, it works. However, plugging it into my XP laptop results in it showing up and being accessible straight away. Strange, but thankfully not that big an issue now I know how to fix it.

Thanks for the replies guys :)

---

