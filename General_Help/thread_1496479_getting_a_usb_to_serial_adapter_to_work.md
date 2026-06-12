---
title: "getting a usb to serial adapter to work"
date: 2010-05-29
forum: General Help
---

### Post by mick463 on 2010-05-29
Hi there another noob question from me the noob  i am studying cisco at the moment and i need a usb to rs-232 converter to get into the console port i have an aten uc-232a converter and i have downloaded a .gz file called uplcom.4freebsd.gz i have unpacked it but i do not know what to do from here could some one please help i need to do some practice for the external icnd 2 exam and i have left it to the last minute as per usual.

---

### Post by beleriand on 2011-08-15
I have the same question.  Do I need to build the uplcom driver somehow?  How do I install it?

---

### Post by beleriand on 2011-08-15
I found that as of Ubuntu 10.4, uplcom driver doesn't need to be built and installed because the pl2303 driver already serves this purpose.  I plugged in my new USB to serial adaptor and got the following for "dmesg":
[ 1295.813075] usb 2-1: new full speed USB device using uhci_hcd and address 4
[ 1295.962551] usb 2-1: configuration #1 chosen from 1 choice
[ 1296.022289] pl2303 2-1:1.0: pl2303 converter detected
[ 1296.043680] usb 2-1: pl2303 converter now attached to ttyUSB0

So then I configured Putty to use ttyUSB0 and then I was able to talk to the serial port :)

---

