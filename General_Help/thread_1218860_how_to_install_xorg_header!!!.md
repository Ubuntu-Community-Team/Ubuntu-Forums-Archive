---
title: "how to install xorg header!!!"
date: 2009-07-21
forum: General Help
---

### Post by shg234 on 2009-07-21
Hi,
I'm a newbie to ubuntu.
While configuring (./configure) my driver source code I got the following error:
```

checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XORG... configure: error: Package requirements (xorg-server >= 1.0.99.901 xproto ) were not met:

No package 'xorg-server' found

```how to overcome it?? can anyone plz lend me a helping hand?

---

### Post by kerry_s on 2009-07-21
```
**sudo apt-get install xserver-xorg-dev**
```

what exactly are you trying to build?

---

### Post by shg234 on 2009-07-23
> **kerry_s said:**
> ```
**sudo apt-get install xserver-xorg-dev**
```
 
what exactly are you trying to build?
 
Thanx for your quick response **Kerry**.
I successfully installed the xorg headers.
 
I am actually try to creating a ubuntu driver for my embedded touch srceen. Now I have a problem with the xorg.conf file. 
 
```

Section    "InputDevice"
    Identifier    "PEL"
    Driver        "PEL"                         ==> The module name: - PEL_drv.so
                                                                   - PEL_drv.la
    Option        "Device"        "/dev/ttyS3"
         ........
         ........

```
 
About the Device option what is the guidline? My device is an USB device. Also which Event I should use? There is Event0 to event6 ...
 
Any help is appreciated in advance.

---

