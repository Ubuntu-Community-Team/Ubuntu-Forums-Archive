---
title: "missing /dev/video0"
date: 2010-11-02
forum: General Help
---

### Post by jruberto on 2010-11-02
and webcam no longer shows up in lsusb (it used to).  generally, the advice is to unplug / replug the camera but mine is built in to my laptop so that's not possible for obvious reasons.

looks like it's initializing okay in dmesg, so (i'm glad) it doesn't look like faulty cable:

```
[   30.468234] Linux video capture interface: v2.00
[   30.476305] uvcvideo: Found UVC 1.00 device CNF7129 (04f2:b071)
[   30.499014] input: CNF7129 as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input9
[   30.499060] usbcore: registered new interface driver uvcvideo
[   30.499062] USB Video Class driver (v0.1.0)
[   33.256370] usb 2-5: USB disconnect, address 2
```
tried manually creating /dev/video0 (with mknod and so forth), and that didn't work.

any suggestions?  thanks!

---

### Post by jruberto on 2010-11-10
solved... sort of.

turns out the cable is bad.  laptop is going back RMA.   ****&#3232;_&#3232;

booted into windows & adjusting the laptop lid angle causes rapid USB connect/disconnect alert sound.

---

