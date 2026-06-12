---
title: "How to add 1360x768 resolution?"
date: 2010-01-14
forum: General Help
---

### Post by Canto39 on 2010-01-14
Hi, I'm using Xubuntu 8.04 Hardy and I have hooked my laptop up to my 32" Vizio 720p LCD HDTV with a VGA cable which is 1366x768 resolution, but that resolution isnt an option on Xubuntu. So how do I add 1360x768 resolution as an option to choose? I know it has something to do with xorg.conf but I dont know what that is or what to do to change it. Help please :)

---

### Post by maxbarjr on 2010-01-14
AFAIK, your video card should also support that resolution, not only your monitor.  And your video card driver too, I guess.

---

### Post by Canto39 on 2010-01-14
So does that mean that if 1360x768 isnt already an option then my video card cant handle it?

---

### Post by Canto39 on 2010-01-15
Can someone answer this for me please?

---

### Post by Leppie on 2010-01-15
you may have to play around with your xorg.conf.
but this also depends on your video card.
you should get the specs like hsync and vsync, etc. and put them in your xorg.conf.
or try to see if there's proprietary drivers available if you have an ati or nvidia card. first run apt-get update:
```
sudo apt-get update
```
then check in Applications>System>Hardware Drivers

---

