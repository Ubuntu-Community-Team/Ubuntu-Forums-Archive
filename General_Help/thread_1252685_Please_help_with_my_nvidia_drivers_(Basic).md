---
title: "Please help with my nvidia drivers (Basic)"
date: 2009-08-29
forum: General Help
---

### Post by mac666 on 2009-08-29
Hey
Im trying to play some games with Wine and PlayOnLinux
how ever the game is saying that i only have 128 mb ram on my gpu, but i have 1024... I have Nvidia GeForce 9800GT

And it cannot start becouse i dont have 3d acceleration and stuff...

Anyone? please help....:confused:

---

### Post by Karloman on 2009-08-29
Did you install the proprietary nvidia drivers?
```
sudo apt-get install nvidia-glx-180
```
Those are the latest available in the repos.
Also have you tried running them with wine instead of playonlinux? I know it sounds weird seeing as playonlinux is basically wine, but it could help.

---

### Post by mac666 on 2009-08-29
yeah i have been trying both POL and wine but none works... it says my videocard doesnt support hardware 3d accelation...

I tried this guid [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
But i dont have anything in my System > Administration > Hardware Drives ... its empety

 What is wrong... All the time i run in to this annoying problems... I JUST WANT TO PLAY :;(

---

### Post by mac666 on 2009-08-29
And i did do that command you gave me... but i allready installed the latest from nvidia website

---

### Post by ks07 on 2009-08-29
Have you checked on the Wine AppDB to see if anybody else has a similar problem? You may find your answer there.

---

### Post by mac666 on 2009-08-29
What is up with my Nvidia drivers. Now can only run my ubuntu in Low Graphics mode...

How do i complety remove all my Nvidia drivers and make a clean install?!?!

---

### Post by uylug on 2009-08-29
Download the latest drivers from the Nvidia site and then

```
sudo bash nvidia_driver_file
```

---

### Post by mac666 on 2009-08-29
> **uylug said:**
> Download the latest drivers from the Nvidia site and then

```
sudo bash nvidia_driver_file
```

I tried this after removing everything i had and it was good after this.. thanks... 
But i cant really get any games to work in wine, it says my video card doesnt have 3d acceleration?

---

### Post by uylug on 2009-08-29
That's weird. Have you tried reinstalling Wine?

Can you enable desktop effects?

---

### Post by mac666 on 2009-08-30
yeah i have reinstalled Wine but still the same problem
I dont have the folder of Direct3D. And i have installed DirectX, .NET packeges etc....


please?

---

### Post by Liolikas on 2009-08-30
Try native games like [http://www.alientrap.org/nexuiz/](http://www.alientrap.org/nexuiz/) they work well?

---

### Post by DJonsson2008 on 2009-08-30
What version of Unbuntu are you running?

Only when I updated to 8.10 was I able to
use Nvidia drivers consistently, 9.4 as
well is much smoother. Problem was 9000 
series was not really compatible with the
8.4 LTS version from what I could figure out.

A fresh install of Unbuntu as well can 
correct at least the basic hardware driver
install and configuration. 
That's been my experience anyhow.

---

### Post by mac666 on 2009-08-30
Well
Warcarft III runs smoothly allmost, so do Fable.
But The games may not change the resolution of the screen...
Like Warcraft III have a resulotion of 1280x*** and my desktop has 1620x*** ... So alot of the screen is black since the program aint allowed to change the resulotion... any ideas?

---

