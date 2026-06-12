---
title: "Maverick, vlc and amarok causing ubuntu to restart."
date: 2010-10-10
forum: General Help
---

### Post by Blue_Alien on 2010-10-10
Whenever I load up vlc player or Amarok after upgrading to 10.10, ubuntu restarts. How can I fix this?

---

### Post by sendblink23 on 2010-10-10
both of them work 100% fine on my 10.10 x64


Maybe you should try a clean install of 10.10 - since you mentioned you did an upgrade (don't forget to back up your data)

---

### Post by Blue_Alien on 2010-10-11
Ok, I did a complete reinstall and it is still crashing when I start vlc. VLC will start up but will log me out of Ubuntu when I roll my mouse into the vlc window.

---

### Post by sendblink23 on 2010-10-11
> **Blue_Alien said:**
> Ok, I did a complete reinstall and it is still crashing when I start vlc. VLC will start up but will log me out of Ubuntu when I roll my mouse into the vlc window.

Then definitely you must be having some hardware problems, or no clue maybe its a driver that is conflicting on your setup

Whats your system specs? And what have you installed after installing 10.10

Look here a screenshot that VLC & Amarok both playing together just fine on my 10.10 x64 
[[IMG]http://img163.imageshack.us/img163/7871/screenshotxkx.th.jpg[/IMG]](http://img163.imageshack.us/img163/7871/screenshotxkx.jpg)
[SIZE="1"]*sorry for having shown that movie there on my screenshot - it is the only video file on my computer to show as a sample for vlc[/SIZE]

---

### Post by Blue_Alien on 2010-10-11
I have an intel 6600 dual core processor and a Nvidia geforce 8800 gts. I have not made any hardware changes since installing 10.10. It is weird that it only happens once the mouse touches the window.

---

### Post by sendblink23 on 2010-10-11
> **Blue_Alien said:**
> I have an intel 6600 dual core processor and a Nvidia geforce 8800 gts. I have not made any hardware changes since installing 10.10. It is weird that it only happens once the mouse touches the window.

Hmm did you install the video driver?
System > Administration > Additional Drivers

That is what I used to make my Nvidia 9800GTX+ to work on my setup(just incase I'm not using my ATI's for Ubuntu)

---

### Post by Blue_Alien on 2010-10-11
I did activate the addition drivers for my graphics card. There are two options, version 173 and version current. I have always used version current in all past ubuntu installs and never had any problems.

---

### Post by sendblink23 on 2010-10-11
> **Blue_Alien said:**
> I did activate the addition drivers for my graphics card. There are two options, version 173 and version current. I have always used version current in all past ubuntu installs and never had any problems.

Since I dont have your same card or hardware... we can't really compare much - on mines I only had the option for installing 260.19.06
Lets hope some GURU can help you out, I see many people around this forum with your same card and not having any issues

---

### Post by Blue_Alien on 2010-10-11
I tried using version 173 and whenever my cursor touches the vlc window, it logs me out of Ubuntu.

UPDATE: Upon complete removal of all Nvidia drivers, vlc does not crash. Is there any way for me to fix this? I've never had any problems with these drivers in previous versions of ubuntu.

---

### Post by Blue_Alien on 2010-10-11
Upon further testing, it appears to only crash when xinerama is enabled. This seems to be a new problem in 10.10.

---

### Post by Notebooks on 2010-10-11
I have the same problem. 
Setup:
Maverick x64
Latest Nvidia driver from nvidia.com. 256.53 I think.
GTX 275
GT 210
4GB ram
Athlon II X2 @ 3.71 GHz

I use xinerama to span my desktop across 3 monitors on 2 cards. As soon as my mouse touches the edge of the vlc window, X restarts and gives me the login screen again.

This might help:
This happens to me in ALL apps that use QT, so I'm guessing that's the culprit, not VLC itself. For example: gnome-mplayer works fine, openshot exhibits the same mouseover crash as vlc.

EDIT: Everything works when I take out my second card and use TwinView, so QT must have a problem with xinerama. I would like to be able to use my 3rd monitor soon, only looking ahead or left is a pain in the neck... literally. :D

I beg the help of the gurus.

---

### Post by bjtuna on 2010-10-14
You're not alone. Please chime in on this bug so it gets the attention it needs.
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/659919](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/659919)

---

### Post by yojimbo-San on 2010-10-14
That's now a duplicate of [https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/650539](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/650539) ... have a look and subscribe/contribute to this report if appropriate.

---

