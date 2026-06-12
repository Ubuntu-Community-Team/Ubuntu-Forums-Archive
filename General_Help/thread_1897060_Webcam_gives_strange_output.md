---
title: "Webcam gives strange output"
date: 2011-12-18
forum: General Help
---

### Post by Weg7DeY8zT on 2011-12-18
Hello all. I installed a new version of my linux (32 bit) and since then the webcam behaves extremely weird.
I get a gray, highly saturated image and I don't know how to fix this.
When I am working with my kinect and the proprietary drivers I get a normal RGB image.

The output looks like this:
[IMG]http://img17.imageshack.us/img17/4594/webcamerror.jpg[/IMG]

The output of lsusb returns:
```

Bus 002 Device 003: ID 0c45:6481 Microdia 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 413c:8160 Dell Computer Corp. 
Bus 001 Device 005: ID 413c:8162 Dell Computer Corp. 
Bus 001 Device 004: ID 413c:8161 Dell Computer Corp. 
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
Is it a hardware problem? Any idea how I could find out?

Thank you.

Best,
  Reinhard

---

### Post by Weg7DeY8zT on 2011-12-18
lsmod | grep video returns this
```

uvcvideo               63695  0 
videobuf2_core         19404  1 uvcvideo
videodev               84035  1 uvcvideo
media                  11283  2 uvcvideo,videodev
videobuf2_vmalloc       1783  1 uvcvideo
videobuf2_memops        2146  1 videobuf2_vmalloc
video                  18712  1 i915
output                  1883  1 vide

```

---

