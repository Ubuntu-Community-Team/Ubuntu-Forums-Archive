---
title: "Webcam unrecognized by cheese/skype"
date: 2012-06-18
forum: General Help
---

### Post by Dapilot1 on 2012-06-18
My aging inspiron 1420n hasn't had any problems before now. Both cheese and skype think I do not have a camera, but the built-in camera is recognized.

```
~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
```

Before 12.04 the camera was recognized by skype 2.2 and cheese, but no longer with 12.04, new skype 4.0, and cheese.

Are there some extra divers I need that don't show in additional drivers?

---

### Post by sanderj on 2012-06-18
Check if the device /dev/video0 exists.

If so, try 

```
vlc v4l2:///dev/video0

```

If not ... I don't know. Maybe something like this:

```
sander@R540:~$ lsmod | grep -i video
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
video                  19596  1 i915
sander@R540:~$

```

Does the cam work if you live boot Ubuntu 11.10? And live-boot Ubuntu 12.04?

---

### Post by Dapilot1 on 2012-06-19
Ha! Worked on 12.04 live usb and worked after a restart.

Guess I was too anxious to use the new release of skype.

Thanks for the ipv6 advise in your sig :)

---

