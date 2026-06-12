---
title: "KDE apps cause Ubuntu 10.10 to crash"
date: 2011-01-05
forum: General Help
---

### Post by angryhomer17 on 2011-01-05
After a fresh install of Ubuntu 10.10 (and all updates applied) any(?) KDE app causes Ubuntu to crash. (X restarts and the login screen is presented.)

This happens immediately when opening kolourpaint, after clicking add file in krename, and after clicking "ok" to set up krusader for the first time.

Any help would be appreciated.

---

### Post by angryhomer17 on 2011-01-06
I decided to do another fresh install to see if something got messed up there. I was able to get kolourpaint to work just fine after the install.

After updating, installing some additional apps, rebooting and launching krusader x crashed again. I figured the likely candidate were the nvidia restricted drivers and I was correct. 

I tried many different combinations of nvidia modaliases versions (96, 173, 180, 185) and each time I opened a kde app, x crashed. Then, I disabled xinerama (since I use two monitors) and the kde apps opened fine.

So, it looks like having xinerama enabled and using kde apps in 10.10 doesn't work very well. I've deactivated the nvidida drivers and am using Ubuntu's monitor config and everything is working ok for now.

Does anyone know why I xinerama and kde apps don't work well together in 10.10? And a second question, am I going to notice any big difference w/o using the nvidia drivers? I don't do much 3d gaming (or much at all) on Ubuntu, but I do a lot of video transcoding. I have a Nvidia GeForce 7600 GT.

Thanks for any help.

---

### Post by berrance on 2011-01-29
BUMP

I also have this same issue, I use KDE as my main desktop, Plus I  use VLC a lot and that also crashes the system.

I think its anything KDE or QT that nvidia doesnt like on more than one moniter

---

### Post by angryhomer17 on 2011-01-29
I was just going to bump this, but it looks like someone else has the same problem. 

I'd really like to be able to use krusader, kolourpaint, and k3b as I use them heavily and have not found better alternatives that I like. Also, without the nvidia drivers I cannot wake up from standby without errors (screen looks like x crashed).

---

### Post by SeijiSensei on 2011-01-29
> **angryhomer17 said:**
> After a fresh install of Ubuntu 10.10 (and all updates applied) any(?) KDE app causes Ubuntu to crash. (X restarts and the login screen is presented.)

Are you installing kubuntu, or ubuntu with KDE installed on top?  I've never encountered these problems starting from kubuntu (10.10 at the moment) and use an NVIDIA 9500GT with the proprietary drivers.

I am having login problems myself.  I can't seem to log in through the graphical interface, but choosing Console Login, and then running startx at the prompt works for me.

I've thought about re-installing or creating a new user to see if there's something funky in my ~/.kde directory, but the machine is up 24/7, so the occasional console login isn't that big of a deal to me.

> **angryhomer17 said:**
> And a second question, am I going to notice any big difference w/o using the nvidia drivers? I don't do much 3d gaming (or much at all) on Ubuntu, but I do a lot of video transcoding. I have a Nvidia GeForce 7600 GT.

The 7600's don't support VDPAU, so they provide no advantage for video.  I'm not sure what you're using for transcoding, but if you talking about converting from one codec/container to another with something like ffmpeg or mencoder, the graphics card isn't involved at all.

KDE does exercise the video card for some plasma effects.  Try turning off Desktop Effects (System Settings > Desktop Effects; uncheck the box at the top) and see if that improves KDE's stability.

---

### Post by angryhomer17 on 2011-01-29
> **SeijiSensei said:**
> Are you installing kubuntu, or ubuntu with KDE installed on top? 

Neither, I just have a vanilla install (Ubuntu with gnome). I can login just fine with the gui and I can run anything but a kde app. 

Like I posted earlier, the kde apps work fine with the nvidia driver only if xinerama is disabled. 

I have dual monitors and need to be able to move windows between screens, which, to my knowledge, is only possible without the nvidia driver, or with the nvidia driver (given that xinerama is installed)

> **SeijiSensei said:**
> The 7600's don't support VDPAU, so they provide no advantage for video. I'm not sure what you're using for transcoding, but if you talking about converting from one codec/container to another with something like ffmpeg or mencoder, the graphics card isn't involved at all.

I use ps3mediaserver which uses mencoder for transcoding, but also handbrake at times which will render the video from scratch.

---

### Post by angryhomer17 on 2011-03-07
I decided to give the nvidia drivers another try today and everything is working just fine now. I'm not sure why they do, but hopefully they'll stay that way.

All I did to solve this was to update and upgrade my packages and install the curent nvidia restricted driver.

I tested krusader, kolourpaint, krename, and k3b. All appear to work normally. Standby functionality is restored and also appears to be working normally.

---

### Post by kelhajjam on 2012-03-29
I have a DELL E640 LATITUDE with Nvidia NVS 4200M, ubuntu 10.10 came  installed and Optimus unchecked. At the beginning I had no problem with  display. Lately I messed up with the nvidia settings. I got my computer  logging off every time I run apps like virtualBox or VLC or Skype...  Other apps works just fine.

I ve been trough everything, I know it is the x server which crashes. I  tried reinstalling the drivers, reconfiguring the xorg.conf. But nothing  works.

Can anyone help me with this problem?

Thank you in advance.

I attach my xorg.conf

---

