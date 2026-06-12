---
title: "Can't get Ubuntu install started"
date: 2012-09-08
forum: General Help
---

### Post by superspartan999 on 2012-09-08
Hey all, I'm trying to install Ubuntu on my PC that I just built (i.e. has no other OS currently on it), but try as I might, I can't any Ubuntu build to install correctly. I've downloaded and tried ubuntu desktop 12.04.1 amd64, i386, gento amd 64 min, and none of them are working which leads me to believe I have a problem in the way I'm creating the boot media. I tried boot CDs and they weren't even being found (granted I just copied and pasted the .iso file on one CD and then tried extracting the contents onto another CD--neither one is recognized). 
My main method has been using a SanDisk USB stick with FAT32 formatting since I can't get FAT16 which sounds like a better format. First I just tried copying and pasting, and I would make it to the screen saying "Try without installing" and all that stuff, but no matter which option I chose, the screen just went black, the HDD made some noise, but nothing else happened. Just a black screen staring back at me. My next attempts were through a couple of Live USB creators -- LiLi and Windows UNetBootin. LiLi would get me to the same point of the copy-paste method, and UNetBootin always gets caught in an infinite loop where my only option is "Default" and when I press Enter, it just starts the 10 second countdown over again. 
I thought the build might be a problem, so I tried the Gentoo distro, and that actually made it all the way to what appeared to be an install process, but it repeatedly hit unskippable errors and never finished. 
Can someone please help me out? I'm trying to move from Windows to Ubuntu, but this is very frustrating.

---

### Post by chellrose on 2012-09-08
I'm not familiar with the USB stick process, but on the CD, copy/paste isn't sufficient.  You have to burn it as a CD image.  What CD burning programs do you have?  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) under the "Windows" section for how to burn the image correctly.

---

### Post by superspartan999 on 2012-09-08
Used PowerISO's burning utility and that worked! Thank you so much!

---

