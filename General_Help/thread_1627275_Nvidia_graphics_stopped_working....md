---
title: "Nvidia graphics stopped working..."
date: 2010-11-21
forum: General Help
---

### Post by noelraxit1 on 2010-11-21
Hi all

guys i'm having a tough time with my graphic card. i have nvidia 8400 GS graphic card and i have installed ubuntu 10.10 and when i update my drivers and restart the PC it literally goes into CLI after the boot and doesn't flash the GUI. i have used all commands like startx, apt-get update but nothing worked...

When i removed my G-card witha fresh copy of os and then updated my drivers everything was fine... guys please help me regarding this issue.....


Thank You

Withs Regards
Noel

---

### Post by sikander3786 on 2010-11-21
Please try,

```
sudo service gdm start
```

It it says it is already running, try,

```
sudo service gdm restart
```

If there are any errors please post them.

You can also try reconfiguring your graphics by,

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then try starting gdm again or press Ctrl + Alt + F7 or simply, reboot and see if it works now.

Another option is to try to reinstall the Nvidia drivers but please update us on the above mentioned commands first.

Good Luck!

---

### Post by noelraxit1 on 2010-11-21
ya sure i'll try and let u know.

---

### Post by lifzunik on 2010-11-21
Once I installed Ubuntu on my laptop, nvidia graphics chip got damaged and I sold my laptop with no use...so be careful

---

### Post by sikander3786 on 2010-11-21
> **lifzunik said:**
> Once I installed Ubuntu on my laptop, nvidia graphics chip got damaged and I sold my laptop with no use...so be careful
In addition to that, please also tell the OP that it was not the fault of Ubuntu either directly or indirectly.

Do you think Ubuntu fried your graphics chipset?

---

### Post by lifzunik on 2010-11-22
Yes it was the fault with Ubuntu... the moment I updated graphics drivers the laptop monitor stopped working and then no go....I installed Windows back to check if it is a driver issue but the chip set got hurt with Ubuntu...

One of them had same issue

check this out 

[http://ubuntuforums.org/showthread.php?t=1319163](http://ubuntuforums.org/showthread.php?t=1319163)

---

### Post by sikander3786 on 2010-11-22
> Yes it was the fault with Ubuntu... the moment I updated graphics drivers the laptop monitor stopped working and then no go....

But don't you think it might be a co-incidence?

I doubt if it was Ubuntu alone that caused the problem. Just a co-incidence as they really do happen in this world :P

---

