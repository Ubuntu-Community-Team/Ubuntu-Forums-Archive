---
title: "Kernel"
date: 2010-11-26
forum: General Help
---

### Post by Diesel_84 on 2010-11-26
Hello, I have an Acer 3610 and I have installed Ubuntu 10.04. Because of my wifi inbuilt card I cannot access internet. If I undersood right I need to install the kernel, I have the root on my desktop but I do not know how to install it.
Can anyone help me please?

---

### Post by sikander3786 on 2010-11-26
Kernel is the thing on which the whole OS runs. As far as the OS is running, kernel is there ;-)

You need appropriate drivers for you card. If you could somehow connect you computer to the internet using a LAN cable, the drivers might automatically pop up under System > Administration > Hardware Drivers.

Or if you can't do that, please list your wifi card make and model.

---

### Post by Hippytaff on 2010-11-26
If you type
```

lspci | grep -i net

```
in a terminal (open a terminal - CTRL+ALT+T) then relay the details of the wirless card (if you can't get online with ethernet) or copy and paste them here if you can, then we can investigate further :-)

---

### Post by dino99 on 2010-11-26
old howto:

[http://ubuntuforums.org/showthread.php?t=285809&highlight=edgy+broadcom](http://ubuntuforums.org/showthread.php?t=285809&highlight=edgy+broadcom)

more recent:

[http://ubuntuforums.org/showthread.php?t=1379320](http://ubuntuforums.org/showthread.php?t=1379320)

[http://www.linuxquestions.org/questions/linux-newbie-8/wireless-network-problem-with-aspire-r3610-linpus-linux-x-789820/](http://www.linuxquestions.org/questions/linux-newbie-8/wireless-network-problem-with-aspire-r3610-linpus-linux-x-789820/)

maybe newest kernel have better result, install 2.6.37 from this ppa:
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

