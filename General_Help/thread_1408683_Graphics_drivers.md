---
title: "Graphics drivers"
date: 2010-02-16
forum: General Help
---

### Post by buhmillion on 2010-02-16
Hello everyone, i have a small question, and i hope it will get answered soon.

I recently bought a Nvidia GT 240 graphics card for my ubuntu desktop, and I cannot find the drivers for it at all. The Nvidia site says that there is not a linux version available, but the manual for the card says there is. I am currently using the Nvidia 195.30 driver, but it crashes intermittently. Where can i find a working Linux x86_64 driver for it?

---

### Post by bodhi.zazen on 2010-02-16
People on this thread :

[http://www.nvnews.net/vbulletin/showthread.php?t=142020](http://www.nvnews.net/vbulletin/showthread.php?t=142020)

report that the nv driver works with that card. The nv driver is the open source nvidia driver.

Additional information is available later in the thread.

---

### Post by gradinaruvasile on 2010-02-16
Well the nv driver is not much help in this case... The guy has a badass card you know. And he wants to use it i guess.

@buhmillion
A bit more details if you can.

What version of Ubuntu are you running?

Did you get the driver from the nvidia's site or installed it from some repository?
In what conditions does the crashes occur - running specific applications, etc?
What type of crash? Hard lock (frozen system), restarting X, crashing apps, black screen etc?

---

### Post by buhmillion on 2010-02-18
I am using 9.10 Karmic, and i got the driver from the NVIDIA site. Is there any way to get the NVIDIA 196.21 driver on ubuntu? I can't find it./

---

### Post by fragos on 2010-02-18
Why didn't you use the driver recommended in System-> Administration-> Hardware Drivers?

---

### Post by gradinaruvasile on 2010-02-19
> **buhmillion said:**
> I am using 9.10 Karmic, and i got the driver from the NVIDIA site. Is there any way to get the NVIDIA 196.21 driver on ubuntu? I can't find it./

That version is the driver for Windows and that works on Windows only. Drivers are platform (Windows, Linux, Mac, etc) specific, you cannot mix and match them.

I have a GF 210 on my work computer, it works perfectly (i now use Debian, but it worked before in Ubuntu 9.10 too) with this driver. 

Also i do not use visual effects (compiz) because i found them buggy sometimes - but, although compiz crashed a lot, very seldom crashed the computer or X.

See the questions i wrote in my previous post and try to answer pls. That might help in determining the root of the problem.


Also, i recommend the following: boot in recovery mode, remove the driver

./drivername --uninstall

and remove /etx/X11/xorg.conf file:

rm /etc/X11/xorg.conf

Then reinstall the driver (while still in recovery mode). Make sure you answer yes to the auto configuring question at the end of the installer script.

Then type:

reboot

and see if it works.


@fragos:
His card is new, the drivers in the Ubuntu repos are a bit older. The latest beta drivers have improvements regarding the newer cards.

---

### Post by fragos on 2010-02-19
> **gradinaruvasile said:**
> 
@fragos:
His card is new, the drivers in the Ubuntu repos are a bit older. The latest beta drivers have improvements regarding the newer cards.

True that is the conventional wisdom which may in some cases be true. Without understanding the actual advantages over the Ubuntu supported driver why not start with a driver that has been tested to work with your system? That was my real point if not well stated. There's nothing wrong with experimenting but with experimenting comes the risk of not working.

---

### Post by gradinaruvasile on 2010-02-19
Well i always used the restricted drivers from the site (on nvidia GF 7600GS, Quadro nvs 285, quadro nvs 135m, GF 210, nvidia IGP 8200, quadro nvs 140m)  and never had problems with it. And i am using it from Ubuntu 7.10, and now on Debian squeeze and works as expected. And this latest beta is as stable as it can get on my 3 computers including the GF 210 card which is from the same line as the 240. 

Thats why i recommend it. Messing around with PPA's is more confusing IMO and may lead to dependency problems in some cases (it did happen to me, and it took  lots of time to clean up the mess - and in case of a beginner i am sure it is worse).
The installer worked on every platform i tried it, and its simple to use.

Yes, you have to reinstall it for every kernel update, but those already require a reboot. And for those who use VDPAU make sure you reinstall the driver if the libvdpau package gets upgraded or you might lose the VDPAU capability.

---

### Post by fragos on 2010-02-19
No PPAs are required for the supported drivers, they're in the Ubuntu repositories set up for users with the Live CD.

---

### Post by 3rdalbum on 2010-02-19
I'm currently using the Nvidia VDPAU PPA, which works very well. I'm using it with a slightly older card (GTX260). Here's how to activate it:

```
sudo add-apt-repository ppa:nvidia-vdpau/ppa
sudo apt-get update
sudo apt-get install nvidia-graphics-drivers-195 nvidia-settings
```

This is a later driver than ships with Ubuntu 9.10 and I believe it should get you up and running with 3D support.

Also, note that it's possible to perform this procedure without touching the command-line - but it's much less convenient.

---

