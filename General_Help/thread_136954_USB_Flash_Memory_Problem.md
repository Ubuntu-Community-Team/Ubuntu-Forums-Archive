---
title: "USB Flash Memory Problem"
date: 2006-02-27
forum: General Help
---

### Post by cgborkgb on 2006-02-27
Hi.  I am having a problem with various usb flash memory devices in Ubuntu 5.10.  I cannot transfer files or properly unmount my Samsung 512MB mp3 player or my NJOY mp3 player (uses a 512MB Kingston SD card).  These devices also do not work in Suse 10.0, but work with no problems on win xp.  On the other hand, I have a Centon 128MB mp3 player that works fine with Ubuntu.  Does anybody have any ideas about what might be wrong?

---

### Post by raghav_p on 2006-02-27
[QUOTE=cgborkgb]Hi.  I am having a problem with various usb flash memory devices in Ubuntu 5.10.  I cannot transfer files or properly unmount my Samsung 512MB mp3 player or my NJOY mp3 player (uses a 512MB Kingston SD card).  These devices also do not work in Suse 10.0, but work with no problems on win xp.  On the other hand, I have a Centon 128MB mp3 player that works fine with Ubuntu.  Does anybody have any ideas about what might be wrong?[/QUOTE]

Some USB Devices are known not to work on Ubuntu and with Linux in general. It might be advisable to purchase a USB Card Reader that works with Linux and use that to transfer data between your mp3 players.

---

### Post by tassou on 2006-03-07
Hi,

I'm having problems as well with some usb mass storage devices that would not unmount cleanly, or mess up during file transfert.
It only happens with "active" devices, i.e. mp3 players, never with usb pens. Surprinsingly I have no problem with the samsung, but some wierd problem with a mpman MP-FUB30 and a genus vizo.
Although it may be possible to use them, most of the time they would mess up in the middle of a file transfert, and the main problem happens when unmounting. The system load reaches 100% and stay there, I'm unable to see which process is responsible for that, and the kernel outputs
 end_request: I/O error, dev sda
continuously. Hard reboot required most of the time (pressing button), because soft reboot stalls.

System : Thinkpad T42 / ubuntu 5.10

Any idea here please ?

Tassou

---

