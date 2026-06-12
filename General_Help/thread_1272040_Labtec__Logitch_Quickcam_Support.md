---
title: "Labtec / Logitch Quickcam Support?"
date: 2009-09-21
forum: General Help
---

### Post by publife on 2009-09-21
Hi All,

I have an old labtec webcam that used to work on a previous install, but now apparently doesn't. I can't get skype or cheese to recognise that it is present.

lsusb shows this

> Bus 002 Device 004: ID 046d:0870 Logitech, Inc. QuickCam Express

and ls /dev/video* gives me

> /dev/video0

and for information, the useful bits of unname -all are:

> 2.6.28-11-generic #42-Ubuntu SMP i686 GNU/Linux

**[This Page]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech")** says there is currently no support for that webcam, but does anyone know of a workaround, however complex?

Thanks!

---

### Post by tgalati4 on 2009-10-31
I got it to work under camorama, but not skype.  I'm running 64-bit Intrepid.

Be sure to:

sudo chmod 777 /dev/video0

It shows up in skype under 32-bit Jaunty after setting user privileges to allow webcam.  System--Admin--Users and Groups.

Does not work with Cheese as it doesn't configure properly with gstreamer-properties.  v4l-info shows its capabilities, but there's a configuration bug that won't allow gstreamer-properties to pick it up.

---

