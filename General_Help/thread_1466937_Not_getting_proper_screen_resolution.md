---
title: "Not getting proper screen resolution"
date: 2010-04-30
forum: General Help
---

### Post by rkrizan on 2010-04-30
My machine is dated, that's for sure, but it's never given me problems. Ubuntu has worked flawless until the 10.04 update. Now I'm not getting my proper screen resolution of 1024.768, and Ubuntu won't recognise my screen. Also, when I try to load up my nvidia drivers on the Hardware Drivers app, and reboot the computer, when GDM loads I get an error that the nvidia module fails to load, and there is no such driver.

Any help would be awesome.

---

### Post by rkrizan on 2010-04-30
This is the output from the error log:

NVIDIA: Failed to load the NVIDIA kernel module. Please check your system's kernel log for addition error messages. 

Failed to load module "nvidia" (module-specific error, 0)

No drivers available.

---

### Post by rkrizan on 2010-04-30
Bump

---

### Post by rkrizan on 2010-04-30
Anyone?

---

### Post by kill4killin on 2010-04-30
Some information about the hardware you're using might help us help you on this one.

Things I can think of off hand that would be useful:

All the graphics card info you know (brand, model, driver, etc)
What monitor are you using (particularly VGA, DVI, HDMI, LCD, CRT, etc)

Normally I would say that your xorg.conf is out of wack, but I don't think that Ubuntu relies on that so much anymore, I believe it's auto-configured at boot or something now :confused: I never really read up on how it works now-a-days

---

### Post by rkrizan on 2010-04-30
It's an Nvidia Geforce3 card. I just did a fresh install, and had to use the "nomodeset" option just to get the LiveCD to work. Ubuntu installed just fine, but I get nothing but a black screen, and have no way of accessing the machine via ssh or otherwise to do some tinkering. 

I don't even see the grub boot menu.

Very odd.

---

### Post by 2hot6ft2 on 2010-04-30
This thread should help. Skip posts #3 and 4.
[http://ubuntuforums.org/showthread.php?t=1465108](http://ubuntuforums.org/showthread.php?t=1465108)

---

