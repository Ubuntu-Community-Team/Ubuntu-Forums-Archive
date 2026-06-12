---
title: "Nvidia GTX 480 SLI + Maverick + Xserver + Pulse woes"
date: 2010-11-01
forum: General Help
---

### Post by CMDR:ZOD on 2010-11-01
Hey everyone this is my first post so I will (try to) keep this pretty short. 
  Ive used ubuntu for a few years now and can now say I am almost 100% Microsoft free. Anyways I recently upgraded my Nvidia 9400 GT videocard for a GTX 480. A big jump I know. After seeing how well it worked in maverick gave me the confidence to buy another. Getting HDMI sound through the onboard sound was a bit of a challenge, but as I say , Its not so much your skill with linux, your googling skills are the important ones. A huge issue was getting vdpau (the nvidia purevideo chip to hardware decode files) to work, which is now partially working after compiling the latest mplayer, smplayer and nvidia vdpau drivers (4.1 I believe). I have noticed the vdpau output is still choppy, mostly on higher quality videos (1080p) with lower quality videos still being easily watchable (driver/ hardware interaction issue I believe). Another issue is that I can no longer enable my creative x-fi soundcard now that pulse and alsa see and are able to use my GTX 480's onboard soundcard. If I enable the x-fi, all sound inputs and outputs are broken and alsa and pulse do not see the creative soundcard anymore. I would really like to be able to enable this as I use txppm and Heli-X to simulate flying rc heli's and my walkera controller works great on the mic in on the front panel input. There are no sound inputs on the GTX 480. Now for the worst problem of buying these top of the line nvidia cards: random freezes. I used to be able to trigger the freezes using vdpau in smplayer, but after compilling all of that from scratch, it will not freeze in that way anymore. Now it crashes less, more randomly, and with no obvious trigger. At the time of crash sometimes there are artifacts on the screen. I am currently using a manual install of nvidia 260.19.12 drivers. For some reason additional drivers will not show anything at all. In my xorg I currently have a line I found online which seems to lessen the amount of random (Xorg)? crashes. The line is:
 
Section "ServerFlags"
 Option "ignoreABI" "True"
EndSection

(Make sure it is at the top of xorg.conf).
The error I find in xlog after a crash:
    10.297] (II) Module dri: vendor="X.Org Foundation"
[    10.297]     compiled for 1.9.0, module version = 1.0.0
[    10.297]     ABI class: X.Org Server Extension, version 4.0
[    10.297] (II) Loading extension XFree86-DRI
[    10.297] (II) LoadModule: "dri2"
[    10.297] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    10.297] (II) Module dri2: vendor="X.Org Foundation"
[    10.297]     compiled for 1.9.0, module version = 1.2.0
[    10.297]     ABI class: X.Org Server Extension, version 4.0
[    10.297] (II) Loading extension DRI2
[    10.297] (II) LoadModule: "nvidia"
[    10.297] (WW) Warning, couldn't open module nvidia
[    10.297] (II) UnloadModule: "nvidia"
[    10.297] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    10.297] (EE) No drivers available.
[    10.297] 
Fatal server error:
[    10.297] no screens found
[    10.297] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    10.297] Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[    10.297] 


My hardware
Asus Rampage II Extreme
Intel core i7 965 Extreme Edition
6GB 1333mhz Ram
Creative X-FI PCIE soundcard
2x Nvidia GTX 480
1000W Enermaxx Galaxy

Any help would be greatly appreciated and I hope this helps (especially newbs, we were all there once)

---

### Post by efflandt on 2010-11-02
Something did not work right, that part should log more like this:

```
[    14.684] (II) LoadModule: "dri"
[    14.684] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.684] (II) Module dri: vendor="X.Org Foundation"
[    14.684]     compiled for 1.9.0, module version = 1.0.0
[    14.684]     ABI class: X.Org Server Extension, version 4.0
[    14.684] (II) Loading extension XFree86-DRI
[    14.684] (II) LoadModule: "dri2"
[    14.684] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.684] (II) Module dri2: vendor="X.Org Foundation"
[    14.684]     compiled for 1.9.0, module version = 1.2.0
[    14.684]     ABI class: X.Org Server Extension, version 4.0
[    14.684] (II) Loading extension DRI2
[    14.684] (II) LoadModule: "nvidia"
[    14.684] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    14.684] (II) Module nvidia: vendor="NVIDIA Corporation"
[    14.684]     compiled for 4.0.2, module version = 1.0.0
[    14.684]     Module class: X.Org Video Driver
[    14.685] (II) NVIDIA dlloader X Driver  260.19.12  Fri Oct  8 11:19:20 PDT 2010
[    14.685] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    14.685] (++) using VT number 7
```

I used the nvidia 260.19.12 from the x-swat repository.  All I had to do was use **remove** from **Additional Drivers** to revert from nvidia 260.19.06 to nouveau, reboot, did the following:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update

Then **activate** nvidia from **Additional Drivers**, reboot, done.

But I have a GT 220, so I have not had any of the GTX issues with any nvidia versions, other than a flood of meaningless errors in /var/log/messages when I was using 260.19.06 that did not affect operation any.

---

### Post by CMDR:ZOD on 2010-11-15
thanks efflandt, I did what you said before but you made me decid to try to get those drivers working and I finally did get it working from the ppa. As you probably know, new drivers came out a couple of days ago, and I did a manual install with them. After disabling Sli it works well enough. I started another thread about the low quality nvidia drivers in the nvidia linux forums as well.

I also started a thread about the compatibility of the gtx onboard hdmi audio device and the supreme fx x-fi (AD1988B). (apparently both use snd-hda-intel and once solved to make x-fi show up in alsa the hdmi audio is broken. I am not sure but believe it might be solvable by setting hdmi card one as always default, but cannot figure out how to do this as both cards use the same codec lol. If you have any ideas please post on my new thread about this issue.

 [http://ubuntuforums.org/showthread.php?p=10120832#post10120832](http://ubuntuforums.org/showthread.php?p=10120832#post10120832)

thanks

---

### Post by CMDR:ZOD on 2010-11-24
Ok Finally got this soundcard working. 
1. Enable X-fi in bios (pci express card, interesting its a bios option mobo: Asus rampage II extreme).

2. Fresh Install of Maverick. Broke audio on my last Maverick installation trying to get this working. 

4. Add the audio-dev ppa for the latest alsa drivers. 
This is the step I had issues with the last maverick installation I had. I had upgraded my kernel to 2.6.35-23 hoping for better alsa only to find I could not use the latest audio-dev ppa drivers. 

5. At this point Alsa found all of my sound devices (3 nvidia gtx 480's with 4 devices each and a pci express supreme fx x-fi with analog and digital out)

Still no sound for the display a 52' plasma connected with and hdmi cable. After quite a while googling I found this line for default.pa that controls pulse audio:

load-module module-alsa-sink device=hw:1,7

and voila sound through the hdmi works! It created a new device in my sound control in ubuntu. Seems to work very well except with one program I have noticed so far... Sid Meiers Alpha Centauri. It used to work fine in the last installation of Maverick. Oh well still an awesome oldschool game.

---

