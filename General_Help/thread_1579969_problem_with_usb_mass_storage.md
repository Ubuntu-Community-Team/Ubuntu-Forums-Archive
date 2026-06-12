---
title: "problem with usb mass storage"
date: 2010-09-22
forum: General Help
---

### Post by the_storm on 2010-09-22
hey guys !
I have a problem with my Ubuntu which is when  I plug my usb mass storage I get nothing as id i haven't plugged it. Nothing appears in the Computer , and when I do the command 
fdisk -l  .. the usb mass storage isn't there to mount it 
and when i  press lsusb
```
Bus 001 Device 009: ID 0951:1625 Kingston Technology 
``` so it's there 
 and here is the dmesg guys 
```
[  321.708020] usb 3-1: device descriptor read/64, error -71
[  321.924013] usb 3-1: new full speed USB device using uhci_hcd and address 3
[  322.044015] usb 3-1: device descriptor read/64, error -71
[  322.268014] usb 3-1: device descriptor read/64, error -71
[  322.484019] usb 3-1: new full speed USB device using uhci_hcd and address 4
[  322.892012] usb 3-1: device not accepting address 4, error -71
[  323.004012] usb 3-1: new full speed USB device using uhci_hcd and address 5
[  323.412012] usb 3-1: device not accepting address 5, error -71
[  323.412028] hub 3-0:1.0: unable to enumerate USB device on port 1

```any help?
my ubuntu is  lucid 10.04
and my mother board is Gigabyte GM31

---

### Post by the_storm on 2010-09-23
guys ...? any help?

---

### Post by btindie on 2010-09-29
I saw a [post]("http://ubuntuforums.org/showthread.php?t=418575&page=3") earlier that suggested
```
modeprobe -r uhci_hcd
```
or take a look at [this]("http://ubuntuforums.org/showthread.php?t=797789") post.

---

