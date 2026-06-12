---
title: "ATI Radeon Help!!"
date: 2011-03-20
forum: General Help
---

### Post by trumpetmaster1 on 2011-03-20
So i am running Ubuntu 10.10 at the moment and i want to know if my ATI Readeon 9550 is running right on Ubuntu. And if it is not installed, can you please help me step by step on how to install all the drivers and things to make my video card run fast and smooth. Thank you

---

### Post by linuxman94 on 2011-03-20
Go to System -> Administration -> Additional Drivers and see if there is a driver available.  If there is, activate it.  If not, then your card is running fine.

---

### Post by Krytarik on 2011-03-20
Unfortunately your card isn't covered by the proprietary driver anymore. But it should nevertheless run fairly good with the Open Source Edge driver:
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```Greetings.

---

### Post by trumpetmaster1 on 2011-03-21
thank you. i think its working. i check glxgears and it said that my video card is working but why am i only getting around 60fps. is there something missing?

---

### Post by trumpetmaster1 on 2011-03-21
> **Krytarik said:**
> Unfortunately your card isn't covered by the proprietary driver anymore. But it should nevertheless run fairly good with the Open Source Edge driver:
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```Greetings.

i tried what you done and i ran glxgears and got this. why am i getting only 60fps? 

sammy@sammy-desktop:~$ glxgears
r300: DRM version: 2.5.0, Name: ATI RV350, ID: 0x4153, GB: 1, Z: 1
r300: GART size: 253 MB, VRAM size: 256 MB
r300: AA compression: NO, Z compression: NO, HiZ: NO
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
290 frames in 5.0 seconds = 57.838 FPS
301 frames in 5.0 seconds = 60.041 FPS
301 frames in 5.0 seconds = 60.040 FPS
301 frames in 5.0 seconds = 60.041 FPS

---

### Post by linuxman94 on 2011-03-21
You need to turn vertical sync off.  Unfortunately, i do not know how on that particular driver

---

### Post by trumpetmaster1 on 2011-03-21
> **linuxman94 said:**
> You need to turn vertical sync off.  Unfortunately, i do not know how on that particular driver

awe :( okay. well i will try to look out for more help and or just research more. sorry. i am very new with ubuntu. thank you very much anyways.

---

### Post by Krytarik on 2011-03-21
> **trumpetmaster1 said:**
> thank you. i think its working. i check glxgears and it said that my video card is working but why am i only getting around 60fps. is there something missing?
"glxgears" can't be taken as an ultimative benchmark. Check it with real applications.

---

### Post by trumpetmaster1 on 2011-03-21
> **Krytarik said:**
> "glxgears" can't be taken as an ultimative benchmark. Check it with real applications.

what kind of apps should i use?

---

### Post by Krytarik on 2011-03-21
> **trumpetmaster1 said:**
> what kind of apps should i use?
The ones you need a speedy video for, I thought you have specific apps in mind, when looking for FPS.

---

### Post by trumpetmaster1 on 2011-03-21
> **Krytarik said:**
> The ones you need a speedy video for, I thought you have specific apps in mind, when looking for FPS.
oh can it be that my monitor causing my fps not go higher?

---

### Post by Krytarik on 2011-03-21
> **trumpetmaster1 said:**
> oh can it be that my monitor causing my fps not go higher?
I really don't know, since I'm not really a FPS-highspeed-video expert. ;-)

---

