---
title: "3g modem problem"
date: 2011-02-02
forum: General Help
---

### Post by L Style on 2011-02-02
I'm using ubuntu 10.04. My Huawei E156G 3g modem doesn't work with ubuntu, It's detect as a storage device not a modem, how can i fix this

---

### Post by msn0 on 2011-02-02
Try using usb-modeswitch. I had a similar problem with Ubuntu 9.10 and Huawei 3g modem. It was quite a long time ago, so I don't exactly remember how I dit it ;)

---

### Post by 3rdalbum on 2011-02-02
These modems act in two (sometimes three) different modes. They act as though they were a CD drive, so Windows users can install the software to drive the modem.

Most of the time, even though the device shows up as a CD-ROM, it will also work as a modem on Ubuntu. You just need to set it up by right-clicking the Network Manager applet and choosing "Edit Connections..." and then go to the Mobile Broadband tab and click Add. Follow the prompts and it should set up.

If that doesn't work, then you can try looking at how to use USB Modeswitch, but don't fiddle with this until you know that your device won't "just work".

---

