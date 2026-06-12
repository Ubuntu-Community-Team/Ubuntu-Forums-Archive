---
title: "Help installing HP Webcam for Ubuntu"
date: 2011-04-19
forum: General Help
---

### Post by ilikejellolol on 2011-04-19
Hey. So I found this webcam lying around, and I ordered the installation disk online and it came in the mail the other day, so I installed it with Wine and got all the programs it came with to work fine. However, I can't get my computer to recognize the webcam when I plug it into the USB port. Does anyone know what I can do to get this thing to work?

---

### Post by mikewhatever on 2011-04-19
You should probably start by figuring out if the system recognizes the device, and also finding out the model, if possible.
Can you open a Terminal window and post the output of **lsusb**.

---

### Post by ilikejellolol on 2011-04-19
vincent@vincent-desktop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 005: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 04f2:a13c Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root h


HP Webcam Deluxe
Product Number KQ246AA
SN CNB950D019

---

### Post by mikewhatever on 2011-04-19
Try launching cheese or skype from a terminal window as follows:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese
```

---

### Post by ilikejellolol on 2011-04-20
Nothing. My webcam has a small blue light on it, and when I connect it to my Windows laptop, the blue light stays lit. When I connect it to my Ubuntu desktop however, the light turns on for a couple of seconds and then turns off.

---

### Post by mikewhatever on 2011-04-20
How about this:
```
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so cheese'
```

You may need to install cheese and skype first.

---

### Post by ilikejellolol on 2011-04-21
That didn't work either. I have the Linux version of Skype installed.

---

### Post by no2498 on 2011-04-21
open a terminal type dmesg click enter

after it stops close the terminal retry cheese

---

