---
title: "USB mount points??"
date: 2009-08-28
forum: General Help
---

### Post by Silvernail on 2009-08-28
I am trying to get a USB device to work.
Using 'lsusb' I get this result:
[B]Bus 005 Device 002: ID 05e1:0408 Syntek Semiconductor Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
[/B]

Looking in my /dev directory I find these:
[B]usbdev1.1_ep00
usbdev1.1_ep81
usbdev2.1_ep00
usbdev2.1_ep81
usbdev3.1_ep00
usbdev3.1_ep81
usbdev4.1_ep00
usbdev4.1_ep81
[/B]
These showed  up after I plugged the device in.
[B]
usbdev5.1_ep00
usbdev5.1_ep81
usbdev5.2_ep00
usbdev5.2_ep81
usbdev5.2_ep82
usbdev5.2_ep84[/B]

Are these the mount points  to my USB devices? Or what. Or based on the results of 'lsusb':
Would that be 'sde2" or 'sdb5' or something entirely different?

I  want to use this device to rip some old cassette tape using the bash shell and most likely this command line.

cat /dev/usbdev5.1_ep81 > videoname.mpg

I'm in the very early stages of this project. so if I don't sound  like I know what I'm doing.  I don't.

Thanks for any feedback you have.
Dave

---

