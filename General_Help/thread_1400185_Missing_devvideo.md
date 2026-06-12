---
title: "Missing /dev/video*"
date: 2010-02-06
forum: General Help
---

### Post by Quindos on 2010-02-06
Anyone out there that can help a novice ?

When connecting a USB-camera
lsusb  correctly gives :
Bus 001 Device 002: ID 041e:4041 Creative Technology, Ltd WebCam Live! Motion
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

which seems to be fairly right (it is a Creative Webcamera)

However, ls /dev/vid* gives :
ls: cannot access /dev/vid*: No such file or directory

Even a systemvide search after video* results in 'nothing' !

What's wrong , where's the video-device , how can I create one ?

---

### Post by jamesisin on 2010-02-06
What is the output of these commands:

```
ls /dev | grep vid*

ls /dev | grep usbdev*
```

---

### Post by Quindos on 2010-02-06
Don't know how to interpret this, but what You suggested give back :

ls /dev | grep vid*
nvidia0
nvidiactl

---

### Post by jamesisin on 2010-02-06
Sorry, I edited my post.  What's the other command give?

---

### Post by Quindos on 2010-02-06
Thank's for replying so fast, I really like this forum :)

ls /dev | grep usbdev  does not return anything  
but :
ls /dev | grep usb*
bus
fuse
usbmon0
usbmon1
usbmon2
usbmon3
usbmon4

Any clue ?

---

### Post by jamesisin on 2010-02-06
First, the nvidea stuff is your video card.

Now Ubuntu made some changes between 8.10 and 9.10 which I am a little unclear about.  On my 8.10 system I have entries like:

```
usbdev1.1_ep00
```

I thought that was maybe bus 1 device 1.  But my 9.10 system (like yours) has entries like:

```
usbmon0
```

This may relate to bus 1, for instance, but I don't see other entries for differentiating between devices on a bus.

(It does appear that my Web cam, which is on Bus 005 Device 002, matches up with usbdev5.2_ep00 or usbdev5.2_ep87 in dev.)

---

