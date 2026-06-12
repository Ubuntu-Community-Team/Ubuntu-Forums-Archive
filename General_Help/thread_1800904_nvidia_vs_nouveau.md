---
title: "nvidia vs nouveau"
date: 2011-07-09
forum: General Help
---

### Post by WendyWeber on 2011-07-09
I was very happy with the drivers that Nvidia provides for my video card on amd64. On 10.10 I did have some issues, and the last upgrade I had in 10.10 broke the drivers, so I had to reinstall the drivers I had before.

Now I upgraded to 11.04, and my video stopped working. I tried to install the Nvidia drivers manually, but they wouldn't install because the Nouveau kernel module was loaded - or something like that. I tried various suggestions to blacklist or remove Nouveau, but the Nvidia driver installer kept complaining. I ended up re-installing Ubuntu. 

Now my video works, but compiz doesn't work. No grid, no wobbly windows, no rotate-cube. I was so happy with my nvidia drivers, why can't I have them on 11.04? 

Christine
If it ain't broke, don't fix it.

---

### Post by LowSky on 2011-07-09
I'm using Nvidia's drivers just fine.

---

### Post by coffeecat on 2011-07-09
> **WendyWeber said:**
> I was so happy with my nvidia drivers, why can't I have them on 11.04? 

You should be able to. I have and they are working just fine with my nvidia card in 11.04. Which nvidia card do you have?

You talk about the nvidia installer. Do you mean the installer downloaded from the nvidia website? Try running the Additional Drivers app. That works for most people. Much simpler than messing about with downloaded drivers.

---

### Post by Blasphemist on 2011-07-09
I agree with the previous post but here is some documentation that may include links helpful to you. [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by wildmanne39 on 2011-07-09
Hi, also when you get your nvidia driver fixed, you can use this guide for setting up the cube and effects in natty, it has pictures for every step and please do not try to set them up with out a guide or you could break unity. I also have nvidia driver install and I have the cube and many effects.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

### Post by Blasphemist on 2011-07-09
> **wildmanne39 said:**
> Hi, also when you get your nvidia driver fixed, you can use this guide for setting up the cube and effects in natty, it has pictures for every step and please do not try to set them up with out a guide or you could break unity. I also have nvidia driver install and I have the cube and many effects.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

That was a darn good tutorial wildmanne!! I've seen others and this was far and away the best.

---

### Post by wildmanne39 on 2011-07-09
> **Blasphemist said:**
> That was a darn good tutorial wildmanne!! I've seen others and this was far and away the best.
Hi, thank you I appreciate it very much a lot of time went into making it and I am thinking about submitting it to the howto forum.

---

### Post by WendyWeber on 2011-07-11
I have an Asus laptop K73SV, it has an Nvidia GT 540M grahpics card. I did a fresh install of ubuntu 11.04, which worked fine. I use "Ubuntu Classic" because I don't like Unity. Also, after instalation, I saw a message that Unity couldn't be started because I didn't have the right hardware. I didn't mind, wasn't going to use Unity anyway. 
Then I activated the nvidia driver through the menu, System/Administration/Additional Drivers. This killed my X. I removed xorg.conf, which gave me back my graphical desktop. The nvidia driver was activated, but not in use. I ran nvidia-xconfig, rebooted, X crashed. I removed xorg.conf again, but then I had a graphical desktop with no upper panel. So I ended up reinstalling ubuntu, which I'm currently doing. I need the laptop starting tomorrow, so I won't do any more experimenting with nvidia, if it works, it works.

I had a similar problem on my desktop computer, I think that was caused by an earlier upgrade in 10.10. One day the upgrade gave me a new nvidia driver, which broke X, so I installed a driver from the Nividia web site, which fixed my system. I take it that this upgrade caused my problems after upgrading to 11.04. I did a fresh install on my desktop computer, I activated the Nvidia drivers through the menu, and it works fine now.

---

### Post by WendyWeber on 2011-07-11
Fresh install of Ubuntu 11.04, first thing after the install I activate the Nvidia driver through System/Administration/Additional drivers, message is "driver is active but not currently in use". Same after restart.

---

### Post by coffeecat on 2011-07-11
> **WendyWeber said:**
> Fresh install of Ubuntu 11.04, first thing after the install I activate the Nvidia driver through System/Administration/Additional drivers, message is "driver is active but not currently in use". Same after restart.

That message is a bug. See my screenshot from a Unity desktop working just fine with the proprietary nvidia driver, whatever additional drivers is trying to tell me. Despite the message, are you able to log into the Unity desktop? Or since you don't like Unity, install compizconfig-settings-manager. Can you enable wobbly windows and other things?

---

