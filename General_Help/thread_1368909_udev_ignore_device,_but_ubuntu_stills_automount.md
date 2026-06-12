---
title: "udev: ignore device, but ubuntu stills automount"
date: 2009-12-31
forum: General Help
---

### Post by Sitron_NO on 2009-12-31
I have a Creative Zen MX, a Garmin GPS and some other devices which I want my Linux to ignore.

I connected the Zen MX, ran 
```
udevadm info -a -p `udevadm info -q path -n /dev/sdd` 
```and got the info I needed.

So I wrote the following rule in */etc/udev/rules.d/10-ignore.rules*:
```
SUBSYSTEM=="usb", ATTRS{serial}=="1A01000141E98C3F0002D900CAA90C3F", OPTIONS=="ignore_device"
```But this does not work. Here is */var/log/syslog*:
```
Dec 31 11:53:22 zero kernel: [   30.065380] usb 1-2.2: configuration #1 chosen from 2 choices
Dec 31 11:53:22 zero kernel: [   30.065915] scsi9 : SCSI emulation for USB Mass Storage devices
Dec 31 11:53:22 zero kernel: [   30.065983] usb-storage: device found at 8
Dec 31 11:53:22 zero kernel: [   30.065985] usb-storage: waiting for device to settle before scanning
Dec 31 11:53:27 zero kernel: [   35.060213] usb-storage: device scan complete
Dec 31 11:53:27 zero kernel: [   35.060665] scsi 9:0:0:0: Direct-Access     Creative ZEN MX           0100 PQ: 0 ANSI: 4
Dec 31 11:53:27 zero kernel: [   35.061032] scsi 9:0:0:1: Direct-Access     Creative ZEN MX MMC       0100 PQ: 0 ANSI: 4
Dec 31 11:53:27 zero kernel: [   35.061347] sd 9:0:0:0: Attached scsi generic sg5 type 0
Dec 31 11:53:27 zero kernel: [   35.061418] sd 9:0:0:1: Attached scsi generic sg6 type 0
Dec 31 11:53:27 zero kernel: [   35.064282] sd 9:0:0:1: [sde] Attached SCSI removable disk
Dec 31 11:53:27 zero kernel: [   35.064655] sd 9:0:0:0: [sdd] 3841152 4096-byte logical blocks: (15.7 GB/14.6 GiB)
Dec 31 11:53:27 zero kernel: [   35.065153] sd 9:0:0:0: [sdd] Write Protect is off
Dec 31 11:53:27 zero kernel: [   35.065155] sd 9:0:0:0: [sdd] Mode Sense: 3e 00 00 00
Dec 31 11:53:27 zero kernel: [   35.065157] sd 9:0:0:0: [sdd] Assuming drive cache: write through
Dec 31 11:53:27 zero kernel: [   35.066283] sd 9:0:0:0: [sdd] 3841152 4096-byte logical blocks: (15.7 GB/14.6 GiB)
Dec 31 11:53:27 zero kernel: [   35.067405] sd 9:0:0:0: [sdd] Assuming drive cache: write through
Dec 31 11:53:27 zero kernel: [   35.067408]  sdd: sdd1
Dec 31 11:53:27 zero kernel: [   35.091152] sd 9:0:0:0: [sdd] 3841152 4096-byte logical blocks: (15.7 GB/14.6 GiB)
Dec 31 11:53:27 zero kernel: [   35.091651] sd 9:0:0:0: [sdd] Assuming drive cache: write through
Dec 31 11:53:27 zero kernel: [   35.091654] sd 9:0:0:0: [sdd] Attached SCSI removable disk
```And Ubuntu automounts the device. The only indication that the rule does work is that *lsusb* does not list the Zen MX no more...

---

### Post by Jemy08 on 2011-04-24
Hi Sitron_NO,

have you had any luck with your zen MX? 
I am in the same situation.
I bought a creative zen mx 16GB. Before I had a creative zen 8GB and could easily work with rhythmbox. 
Now, when I connect my zen mx, it opens up like a regular usb drive and I can navigate through the folders, but it is not recognized by rhythmbox.

I tried different solutions, i.e. adding the device in 
/lib/udev/rules.d/45-libmtp8.rules

or trying your solution, but nothing works..

Obviously some users have no problem with the creative zen mx. That's why I thought it might be a firmware issue (newer firmwares are not recognized by ubuntu...). But I can't find any older firmware to install from the creative website.

any more suggestion?

cheers

---

