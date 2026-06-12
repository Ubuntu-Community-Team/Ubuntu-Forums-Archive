---
title: "Syntek webcam driver loaded but not working"
date: 2009-11-21
forum: General Help
---

### Post by The Judderman on 2009-11-21
Dear all,

I have an ASUS laptop with integrated syntek webcam that I have had problems getting to work in all variants so far.

I have managed to load the module into the kernel using this forum ([http://doc.ubuntu-fr.org/syntek]("http://doc.ubuntu-fr.org/syntek")) but it doesn't work in any app (skype, amsn, camorama, cheese)

These are some of the logs. Any others that would be useful?

> dmesg | grep stk11xx

[    6.732475] stk11xx: Syntek USB2.0 webcam driver startup
[    6.732504] stk11xx: Syntek USB2.0 - STK-1135 based webcam found.
[    6.732506] stk11xx: Syntek AVStream USB2.0 1.3M WebCam - Product ID 0x6A31.
[    6.732510] stk11xx: Release: 0005
[    6.732513] stk11xx: Number of interfaces : 1
[    6.735437] stk11xx: Initialize USB2.0 Syntek Camera
[    6.844145] stk11xx: Check device return error (0x0201 = 0C) !
[    6.908141] stk11xx: Syntek USB2.0 Camera is ready
[    6.908222] stk11xx: Syntek USB2.0 Camera is now controlling video device /dev/video0
[    6.908265] usbcore: registered new interface driver usb_stk11xx_driver
[    6.908270] stk11xx: v1.3.1 : Syntek USB Video Camera
[    6.973767] Modules linked in: x_tables snd_seq_device ath stk11xx snd videodev asus_laptop soundcore v4l1_compat cfg80211 snd_page_alloc led_class psmouse serio_raw dm_raid45 xor usb_storage fbcon tileblit font bitblit softcursor vesafb video output radeon ttm drm i2c_algo_bit 8139too 8139cp mii sis_agp agpgart
[    6.973870]  [<f88e142d>] ? v4l_stk11xx_ioctl+0x1d/0x1030 [stk11xx]


> sudo lsusb -v|grep -A 8 Syntek
 
Bus 001 Device 002: ID 174f:6a31 Syntek Web Cam - Asus A8J, F3S, F5R, VX2S, V1S
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x174f Syntek
  idProduct          0x6a31 Web Cam - Asus A8J, F3S, F5R, VX2S, V1S
  bcdDevice            0.05
  iManufacturer           1 
  iProduct                2 
  iSerial                10 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9


I think this all means that the module is loaded and that it is linked to /dev/video. So why doesn't it work?!?

I have tried running skype and camorama as root (gksudo) to see if that changes anything, but to no avail!

Any thoughts?

The Judderman

---

### Post by The Judderman on 2009-11-25
I solved this issue.

I had to cleanly reinstall Karmic because of stupidity, and on a clean install, I just followed the svn instructions and magically it worked!

So now I have a syntek webcam working!!! Hurrah!

The Judderman

---

