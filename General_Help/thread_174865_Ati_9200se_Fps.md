---
title: "Ati 9200se Fps"
date: 2006-05-12
forum: General Help
---

### Post by seth0x2b on 2006-05-12
Hey guys.
I installed Ubuntu Hoary 2 days ago.I managed to setup fglrx with no problem following theese instruction [http://ubuntuforums.org/showthread.php?t=143283&highlight=mesa+issue](http://ubuntuforums.org/showthread.php?t=143283&highlight=mesa+issue)
Since I have an ATI Radeon 9200SE, getting 800 or so FPS was a blessing( I've used Fedora for about 1.5 years and I couldn't get the damn drivers to install...got Ubuntu and 2 hours later I was installing Maya 7 ](*,)  ).
I did a dist-upgrade today(to breezy) I folowed the exact same instructions as above, the driver is installed, but I get only 130 or so FPS.
```
seth@orion:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200SE DDR Generic
OpenGL version string: 1.3.1010 (X4.3.0-8.16.20)

```
```
seth@orion:~$ fgl_glxgears
676 frames in 5.0 seconds = 135.200 FPS
716 frames in 5.0 seconds = 143.200 FPS
750 frames in 5.0 seconds = 150.000 FPS
706 frames in 5.0 seconds = 141.200 FPS

```
I searched and searched the forum and still couldn't find anything.
Since I use the computer for 3D modelling and would like to use it to play Neverwinter too, I really have to get this fixed.

Thanks in advance

---

### Post by seth0x2b on 2006-05-13
I hate to bump this thread but I really need some advice.
It's been 1 day already without Maya and I really need it :(

Cheers

---

### Post by ifokkema on 2006-07-28
Hi,

Did you find any help? I've got the same video card, and attempts at getting fglrx to work has frozen my system more than once. I gave up and started using the default Breezy ATI driver, but just now and then my system would halt suddenly. After some searching, I disabled all DRI, GLX and whatnot from the Xserver config. Now it doesn't freeze anymore, but I still haven't got any direct redering. I will upgrade to Dapper soon, and see if that works.

---

