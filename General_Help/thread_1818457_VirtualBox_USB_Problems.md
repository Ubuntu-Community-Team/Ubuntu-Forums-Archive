---
title: "VirtualBox USB Problems"
date: 2011-08-04
forum: General Help
---

### Post by SwarfEye on 2011-08-04
Hi all.

I've been developing for the avr on ubuntu for years now.

I've gotten a new macbook and I have installed ubuntu 11.04 as a guest system using Virtual Box.

For some reason, I am unable to see my usb JTAG mkii when I plug it in to the usb port.

I have made a USB filter, and it is clear that the ubuntu system is seeing the device.  When I run...
```
 tail -f /var/log/syslog
```
then plug in the Jtag, I get
```
Aug  4 16:39:31 VirtualUbuntu kernel: [ 1349.315385] usb 1-2: USB disconnect, address 3
Aug  4 16:39:41 VirtualUbuntu kernel: [ 1358.493049] usb 1-2: new full speed USB device using ohci_hcd and address 4
```
which looks good to me.
also... when I run lsusb with the jtag in I get...
```
username@VirtualUbuntu:~$ lsusb
Bus 001 Device 004: ID 03eb:2103 Atmel Corp. JTAG ICE mkII
Bus 001 Device 002: ID 80ee:0021  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
but I don't seem to get a devname!!
I've tried using
```
/dev/vboxusb/001/004
```
... but I just get an error.

Any suggestions?

Thanks,

B

---

### Post by gordintoronto on 2011-08-05
Did you install Virtualbox from the Oracle site? Did you install the extension?

---

### Post by coldraven on 2011-08-05
In my case, Ubuntu host with XP guest, the USB did not work until I added myself to the vboxusers group in "Users and Groups". You then need to log-out and back in or re-boot.
I'm not sure if this still applies in VBox 4.1.

---

