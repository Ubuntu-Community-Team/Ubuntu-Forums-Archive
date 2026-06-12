---
title: "USB/serial permissions kstars"
date: 2012-07-12
forum: General Help
---

### Post by fewjr on 2012-07-12
Hello All,
I hope this question is okay in the general section. I am using maverick meerkat 10.10 and I am trying to control a meade ETX-80 telescope with Kstars, version 1.6.0. My laptop has no serial connections, so I am using a usb/serial adapter/cable which is of the Prolific PL2303 type.

Here is the output of sudo lsusb

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 187c:0514  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 064e:8101 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 

When I try to connect to the telescope it tells me to set permissions to read and write. Permissions are only set for root right now I suppose. I need to know how to set read/write permissions for /dev/ttyUSB0 on my user account to see if Kstars is going to work. I have Stellarium working with all this hardware in Win7 but want to use Ubuntu for this. Any help would be greatly appreciated.

Thanks in advance,
fewjr

---

### Post by fewjr on 2012-07-12
I have continued to try to get this myself. This is what I have tried so far, but 1st a few more command outputs from the terminal:

sudo tail -f /var/log/messages shows this when I plug in my usb to serial cable (Prolific).

Jul 12 16:43:15 goblinbox-alien kernel: [15096.916239] usb 4-1: new full speed USB device using uhci_hcd and address 4
Jul 12 16:43:15 goblinbox-alien kernel: [15097.078341] pl2303 4-1:1.0: pl2303 converter detected
Jul 12 16:43:15 goblinbox-alien kernel: [15097.090410] usb 4-1: pl2303 converter now attached to ttyUSB0

Also this

~$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[    0.898865] tty tty15: hash matches
[   14.969188] usb 4-1: pl2303 converter now attached to ttyUSB0
[ 2246.830960] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[ 2247.120469] usb 4-1: pl2303 converter now attached to ttyUSB0
[15064.928919] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[15097.090410] usb 4-1: pl2303 converter now attached to ttyUSB0
[15742.464625] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[15758.884314] usb 4-1: pl2303 converter now attached to ttyUSB0


I also tried writing a file as root- 

/etc/udev/rules.d/50-udev.rules

I put this in the file-

KERNEL=="ttyUSB[0-9]*",NAME="tts/USB%n",SYMLINK+="%k",GROUP="uucp",MODE="0660"

Still not having any luck.

fewjr

---

### Post by ulrith on 2012-12-25
Hi fewjr!

I'm happy owner of etx-80 also and trying to connect to it through Kstars.
Could you please tell me what telescope model you have selected from the list of available ones because there is no such item as ETX-80?

---

