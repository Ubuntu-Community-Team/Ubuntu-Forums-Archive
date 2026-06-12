---
title: "First timer install issues"
date: 2010-03-10
forum: General Help
---

### Post by bunkie21 on 2010-03-10
Hello all,

I have recently found Ubuntu and already like what I see and appreciate that its not Windows.  However, I am having several issues that I just cant seem to fix. 

The first would be my USB Belkin adapter (f5d8053).  I have done (or tried) to do everything I can find on the net but with no luck.  Today I finally just broke down and bought an adapter that is said to work (spending money for a free OS).

Second, when I loaded Ubuntu from the CD to "try" it, it popped up a hardware window that gave me options to install drivers for my Nvidia 8800 GTS VC.  When I installed Ubuntu it dosent pop up any options to select drivers like it did when I was checking it out and I cant enable any of the graphics options.  I finally found jockey-gtk and it now says that there are no drivers avaliable... so Im lost.

Keep in mind any option most likey needs to be done without internet connectivity (from within Ubuntu).

Thanks for any help,

Dustin

---

### Post by prodigy_ on 2010-03-11
Searching the forum first could probably save you money:
[http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)

Official (proprietary) nVidia drivers you can get here:
[http://www.nvidia.com/object/linux_display_ia32_190.53.html](http://www.nvidia.com/object/linux_display_ia32_190.53.html) (32-bit version).
[http://www.nvidia.com/object/linux_display_amd64_190.53.html](http://www.nvidia.com/object/linux_display_amd64_190.53.html) (64-bit version).

Hope that helps.

---

### Post by bunkie21 on 2010-03-11
Thanks the info and links,  I will give it a try tonight.  However, I do still have a concern about why at one time it appears to be working correctly then I install it and it dosent work.  Did it not get installed right?  Is there a larger issue for me?

---

### Post by bunkie21 on 2010-03-11
Ok, so I still cant get the usb adapter working.  I have given up on it.

I try to run the NVIDIA file and it pops up several options.  I click run and it does nothing.  I click run in terminal and it show an install screen but says that it must be installed by root.  I dont know how to log into root...  I think something is wrong with my install.

---

### Post by bunkie21 on 2010-03-11
Ok, so I figured out how to use sh ./NVIDIA-Linux..., but now it says that X Server is on and to turn it off. 

It seems that if Linux works it works good but if it does not work it is just absolutely terrible.  For new users anyways.

Any hints anyone?

Thanks
-------------------------------------

Never mind, got the NVIDIA driver working.

---

### Post by prodigy_ on 2010-03-12
First of all, you don't need to login as root. There's "sudo" command. So your command line will be something like:
```
sudo sh ./NVIDIA-Linux-x86-190.53.run
```

Also, to make the installation easier, you can use nVidia VDPAU repository. Use the following commands:
```
sudo add-apt-repository ppa:nvidia-vdpau/ppa
```
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767
```
```
sudo apt-get update
```
```
sudo apt-get install nvidia-190-modaliases nvidia-glx-190 nvidia-settings-190
```

Hope that helps.

---

You're somewhat right about Linux. Any OS requires certain degree of knowledge. Otherwise some things won't work as you expect/want them to work. And today Linux is much friendlier than it was, say, 5 years ago. Gradually, things are getting better for the newcomers.

---

