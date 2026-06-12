---
title: "create a symlink after a SD card inserted"
date: 2010-09-29
forum: General Help
---

### Post by Roy.Zhang on 2010-09-29
I want to use a script to analyze some files content if there is a SD card inserted into system. And in my ubuntu desktop edition, there will be a link create on desktop named as SD card label after the SD card is inserted. To be simplify, I want to create a unique link for all sd card with difference label. so I use the udev script like below for a test:

```
ACTION=="add", SUBSYSTEMS=="usb", ATTR{removable}=="1", SYMLINK+="/usblink", MODE="0666"
```

Actually, there is no /usblink created after I insert my sd card.
And in udev manual, there is not much enough information for me to diagnoze this problem.
Can anybody help me on this.
Thanks very much

---

