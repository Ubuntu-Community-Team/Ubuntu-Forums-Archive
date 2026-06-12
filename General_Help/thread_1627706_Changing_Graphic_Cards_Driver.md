---
title: "Changing Graphic Cards Driver"
date: 2010-11-21
forum: General Help
---

### Post by balta on 2010-11-21
Hallo everyone!
So, a very simple question.
I'm currently using windows 7 on my computer, I have an ATI GPU and I am willing to install Ubuntu to finally rock it out.
However I'm going to change my video card for a newer nVidia one in a few weeks and I'm wondering about the drivers change...
Under windows it should be quite simple however I'm quite afraid of possible issues I could have under Ubuntu.
Probably (I believe and hope) everything will just work fine, simply plug and play, no conflicts, nothing at all.
However I'm asking because I would like to avoid any issues, as I prefer dealing with windows one month or so more than having driver issues under ubuntu...

Resume: is it possible that changing GPU (brand) generates driver issue under ubuntu 10.10?

thanks for your time

---

### Post by gordintoronto on 2010-11-21
Don't install a proprietary driver, and you should be OK.

---

### Post by papibe on 2010-11-21
Considering you'll have lots of benefits running an nvidia card, I would recommend the hardware update.

First before installing the card, reset your X settings by removing (or renaming) your xorg.conf:
```
$ sudo mv /etc/xorg.conf /etc/xorg.conf.old
```
When you have the card installed, go to System -> Administration -> Hardware Drivers. There, install (or activate) the nvidia driver. Probably you'll need to reboot to take effect.

After that you can tune your settings using System -> Administration -> Nvidia X Server Settings.

Good Luck!

---

### Post by balta on 2010-11-22
Thanks! I'll post here the results and the procedure I will have followed as soon as I receive the nVidia.

---

