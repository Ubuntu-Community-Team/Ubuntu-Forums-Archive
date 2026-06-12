---
title: "saving resolutions for nvidia on 9.10 Karmic Koala"
date: 2009-10-29
forum: General Help
---

### Post by aljoriz on 2009-10-29
this assumes that you have install the nvidia driver.  

at the terminal type:
sudo rm /etc/X11/xorg.conf
then:
gksu nvidia-settings
(write password)
go to X server display configuration adjust to the desired resolution>APPLY>SAVE TO XCONFIG

Now write this on the save X box:
/etc/X11/xorg.conf

press save and you are done ... found this on the web upd8 blog.  Hope this helped someone

---

### Post by stooby on 2009-11-03
thank you - perfect solution to my problem

---

### Post by Darth Trix on 2009-11-08
Thanks. I had the same problem, perfect solution, thanks again

---

### Post by LOGM on 2009-12-03
So did I! Thankyou!

---

### Post by Phonic_P on 2009-12-07
I've done a fresh install of kubuntu 9.10 it dose not have an xorg.config file! Any options for me???

---

### Post by blueridgedog on 2009-12-07
> **Phonic_P said:**
> I've done a fresh install of kubuntu 9.10 it dose not have an xorg.config file! Any options for me???

Then you can omit the delete step.

---

### Post by aljoriz on 2009-12-23
a fresh install does not have a etc/x11/xorg.conf

so you still have to do the last part, I think

Funny that I switched to Linux Mint and this trick still works like a charm

---

