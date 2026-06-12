---
title: "Lucid no longer booting"
date: 2010-05-04
forum: General Help
---

### Post by nmandryk on 2010-05-04
I upgraded my laptop from 8.04 Hardy to 10.04 Lucid on Saturday. No problems in the upgrade. The minor fixes I had to make were things like reconfiguring my shortcut keys and keyboard settings.

Since last night I haven't been able to boot into Ubuntu. It hangs in the booting process doing nothing, and I end up having to do a hard power off. The only thing I can think of that may have caused this is that in my previous session, I changed my keyboard layout and chose 'Apply systemwide'. Is there any chance that could have caused a boot problem?

I'm not able to boot into either version of the kernel that shows up in GRUB or into their equivalent Recovery versions. I'm able to use my Vista partition, however.

I'd appreciate any help!

---

### Post by nmandryk on 2010-05-04
Here's what I can see on my laptop screen. It consistently freezes at this point.

[  9.735305] TCP cubic registered
[  9.735495] NET: Registered protocol family 10
[  9.736050] lo: Disabled Privacy Extensions
[  9.736414] NET: Registered protocol family 17
[  9.736518] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-60 processors (2 cpu cores) (version 2.20.00)
[  9.736642] powernow-k8:  0: fid 0xc (2000 MHz), vid 0x11
[  9.736704] powernow-k8:  1 : fid 0xa (1800 MHz), vid 0x12
[  9.736766] powernow-k8:  2 : fid 0x8 (1600 MHz), vid 0x13
[  9.736828] powernow-k8:  3: fid 0x0 (800 MHz), vid 0x1e
[  9.737053] PM: Resume from disk failed.
[  9.737125] registered taskstats version 1
[  9.737560] Magic number: 10:516:322 
[  9.737638] tty tty47: hash matches
[  9.737708] misc mcelog : hash matches
[  9.737774] ehci_hcd 0000:00:02.1: hash matches
[  9.737894] rtc_cmos 00:07: setting system clock to 2010-05-04 09:19:34 UTC(1272964774)
[  9.737969] BIOS EDD facility v0.16 2004-jUN-25, 0 devices found
[  9.738031] EDD information not available
[  9.753330] input: AT Translated Set 2 Keyboard as /devices/platform/i8042/serio0/input/input5
[  9.870036] usb 2-2: new high speed USB device using ehci_hcd and address 2
[ 10.034136] usb-2.2: configuration #1 chosen from 1 device

---

### Post by Peter Jenkins on 2010-05-18
I have a *very* similiar boot screen, showing no intention to proceed the booting. But I can't say that it has hanged, as it reacts to attaching/removing of USB device, and to the WIFI switch. It will also reboot on ctrl+alt+delete. 

I also remember pressing 'Apply systemwide..' on the keyboard layout setup window.

---

### Post by Peter Jenkins on 2010-05-19
I was able to boot with older version of kernel, "Ubuntu, with Linux 2.6.31-21-generic" and then "Reset to Defaults" on the Keyboard Preferences -> Layouts tab. 

Until this was done, I was unable to boot with the newer 2.6.32-22 kernel, which is loaded at the moment. I'm going to try and reproduce that boot failure once again.

---

### Post by nmandryk on 2010-06-18
I was unable to boot with an older version of the kernel. However, I have since completed a fresh 10.04 install and have not experienced any significant trouble.

---

