---
title: "Printer stopped working"
date: 2011-05-21
forum: General Help
---

### Post by Rich_S on 2011-05-21
Running Ubuntu 10.04.  Printer is an HP Laser Jet 1100 parallel, running over a parallel to USB cable.

It has worked fine for years.  Have not made any config changes.  One of the System Updates over the past few weeks must have done something to break it.


Log:

May 21 09:57:34 rich-desktop kernel: [1622258.794542] usb 1-5.2: usbfs: interface 0 claimed by uss720 while 'usb' sets config #1
May 21 09:57:39 rich-desktop kernel: [1622263.795979] usb 1-5.2: usbfs: interface 0 claimed by uss720 while 'usb' sets config #1
May 21 09:57:44 rich-desktop kernel: [1622268.796969] usb 1-5.2: usbfs: interface 0 claimed by uss720 while 'usb' sets config #1
May 21 09:57:49 rich-desktop kernel: [1622273.797801] usb 1-5.2: usbfs: interface 0 claimed by uss720 while 'usb' sets config #1
May 21 09:57:54 rich-desktop kernel: [1622278.798663] usb 1-5.2: usbfs: interface 0 claimed by uss720 while 'usb' sets config #1
May 21 09:57:59 rich-desktop kernel: [1622283.799256] usb 1-5.2: usbfs: interface 0 claimed by uss720 while 'usb' sets config #1
May 21 09:58:04 rich-desktop kernel: [1622288.800051] usb 1-5.2: usbfs: interface 0 claimed by uss720 while 'usb' sets config #1
May 21 09:58:09 rich-desktop kernel: [1622293.800878] usb 1-5.2: usbfs: interface 0 claimed by uss720 while 'usb' sets config #1
May 21 09:58:14 rich-desktop kernel: [1622298.801708] usb 1-5.2: usbfs: interface 0 claimed by uss720 while 'usb' sets config #1
May 21 09:58:19 rich-desktop kernel: [1622303.802522] usb 1-5.2: usbfs: interface 0 claimed by uss720 while 'usb' sets config #1
May 21 09:58:24 rich-desktop kernel: [1622308.803390] usb 1-5.2: usbfs: interface 0 claimed by uss720 while 'usb' sets config #1
May 21 09:58:29 rich-desktop kernel: [1622313.804199] usb 1-5.2: usbfs: interface 0 claimed by uss720 while 'usb' sets config #1
May 21 09:58:34 rich-desktop kernel: [1622318.805006] usb 1-5.2: usbfs: interface 0 claimed by uss720 while 'usb' sets config #1
May 21 09:58:36 rich-desktop kernel: [1622321.486513] usb 1-5.2: USB disconnect, address 17
May 21 10:01:12 rich-desktop kernel: [1622477.060106] usb 1-5.1: new full speed USB device using ehci_hcd and address 19
May 21 10:01:12 rich-desktop kernel: [1622477.157963] usb 1-5.1: configuration #1 chosen from 1 choice
May 21 10:01:13 rich-desktop kernel: [1622478.156012] get_1284_register timeout
May 21 10:01:14 rich-desktop kernel: [1622479.156511] get_1284_register timeout
May 21 10:01:15 rich-desktop kernel: [1622480.156509] get_1284_register timeout
May 21 10:01:16 rich-desktop kernel: [1622481.156509] get_1284_register timeout
May 21 10:01:17 rich-desktop kernel: [1622482.156510] get_1284_register timeout
May 21 10:01:17 rich-desktop kernel: [1622482.157026] get_1284_register: usb error -32
May 21 10:01:18 rich-desktop kernel: [1622483.156011] get_1284_register timeout
May 21 10:01:18 rich-desktop kernel: [1622483.156537] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.216009] get_1284_register timeout
May 21 10:01:19 rich-desktop kernel: [1622484.216667] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.216917] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.217167] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.217416] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.217666] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.217917] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.218167] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.218416] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.218666] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.218916] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.219166] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.219416] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.219666] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.219916] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.220166] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.220721] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.220921] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.221167] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.221416] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.221666] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.221916] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.222166] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.222415] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.222666] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.222916] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.356156] get_1284_register: usb error -32
May 21 10:01:19 rich-desktop kernel: [1622484.368026] parport4: fix this legacy no-device port driver!
May 21 10:01:19 rich-desktop kernel: [1622484.369304] lp4: using parport4 (polling).

---

### Post by Rich_S on 2011-05-28
Any ideas?

---

