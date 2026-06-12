---
title: "help translating some fixes found on forum"
date: 2012-05-23
forum: General Help
---

### Post by cristian.ene on 2012-05-23
can anyone please translate into "noobish" the following? 

```
                        nvidia-173 drivers are not compatible with Xorg (ABI to be precise) version released in 12.04.
So I stick with 11.10 version of Xorg. I had to make the following changes to backport Xorg:
 In /etc/apt/sources.list :
 deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric main
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric main
 In /etc/apt/preferences:
 Package: xserver-xorg*
Pin: release a=oneiric
Pin-Priority: 1050
 Note related to nvidia-173 on Ubuntu 12.04:
I'm using old hardware with nvidia-173 drivers and I don't like the fact  "composite" is mandatory to use Unity correctly (very laggy) I had to  force composite to switch it "off" to avoid laggy windows by modifying  /etc/X11/xorg.conf:
 Section "Extensions"
    Option             "Composite" "Disable"
EndSection

              

```the /etc/apt/sources.list, i edited and saved...
next?!? what do i do?

---

### Post by cristian.ene on 2012-05-23
bump!

---

### Post by oldos2er on 2012-05-23
Please wait 24 hours between bumps.

---

### Post by cristian.ene on 2012-05-24
sorry,.. didn't knew that :)

---

### Post by steeldriver on 2012-05-24
Have a look here if you want a clearer explanation of pinning and holding packages:

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

The other part is about creating a custom xorg.conf file

---

