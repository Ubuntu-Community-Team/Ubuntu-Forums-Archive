---
title: "monitor problem"
date: 2011-08-24
forum: General Help
---

### Post by vkeifreek on 2011-08-24
Ok I have a Kogi L7EH-TA 17 in. lcd monitor and im running a fresh install of ubuntu 11.04 64bit. When I first Boot up everything looks fine about 5 seconds later it goes black and I get a box that either says "oversize recommand mode 1280x1024" or "out of range" the monitor then goes into standby and nothing happens after that. I hook up an older monitor and everything works fine. I've tried using google to find a possible solution but nothing I have tried has worked. Any help would be greatly appreciated.

---

### Post by kartabosh on 2011-08-24
alt+f2
> gksu gedit /boot/grub/grub.cfg
change 
line 47
from 
  set gfxmode=auto
to 
  set gfxmode=640x480

---

### Post by vkeifreek on 2011-08-24
> **kartabosh said:**
> alt+f2

change 
line 47
from 
  set gfxmode=auto
to 
  set gfxmode=640x480

Thank you but when I tried that the monitor stayed up for a few seconds longer then went into stand by just as it did before.

---

### Post by vkeifreek on 2011-08-24
Any ideas anyone?

---

### Post by vkeifreek on 2011-08-25
Am I not able to use this monitor or something?

---

