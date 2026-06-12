---
title: "Mic Doesn't work in 10.04"
date: 2010-04-30
forum: General Help
---

### Post by zaphod777 on 2010-04-30
I just wanted to post here to let anyone know how to fix a broken Mic in 10.04. I have an XPS m1530 and was running RC and updating. This was a big problem since I use Skype a lot to talk to freinds and family out of country. 

I fixed it by removing and re-installing Alsa but this may not be a problem for people installing from the final release ISO.

here are the commands you need to run 

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils 
sudo apt-get install linux-sound-base alsa-base alsa-utils 
sudo apt-get install gdm ubuntu-desktop 
```

Then reboot and enjoy!

---

### Post by JoshOrndorff on 2010-05-09
Thanks for the info.  I always like it when I find a post with a solution before anyone even asked about the problem.  I thought I'd mention that I upgraded from 9.10 using the final release iso, and still had the problem.  I purged the packages you mentioned and reinstalled them, but I did not have to use the third command to install gdm or ubuntu-desktop.

Thanks a lot.

-Josh

---

### Post by zaphod777 on 2010-05-09
I am happy I was able to help someone this was driving me nuts for a while until I fixed it. I tried many other solutions that didn't work until this one.

---

### Post by webified on 2010-05-10
Thank you zaphod777!

I've been searching on and off all week (since upgrading to 10.04) for a fix to my sound and this solved my problem. For the sake of others:
Dell studio 1555 with :
Audio device: ATI Technologies Inc RV710/730
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Plus, I did:
apt-get install linux-backports-modules-alsa-lucid-generic
from another post. I think I'll leave that in place for now.

Thanks again. I can now skype to my family and friends back home.

---

### Post by dalee on 2010-05-10
Hi,

Just to add to the possible solutions to try. Using 10.04 on an eeePC 1101HC. I simply installed the linux-backports-modules-alsa-lucid-generic as recommended by webified.

I then was able to use sound recorder to record. But still no sound in Skype. A quick search of the Ubuntu community Docs showed that pulse is looking for stereo recording. And when it encounters a mono mic, it shuts the mic off. To re-enable it, make sure the sliders in puav control are unlocked. Then just reduce one of the volume controls by about 10% or so. My mic is now functional for Skype.

dalee

---

### Post by brammert on 2010-05-11
Thanks, worked for kubuntu as well! You are a real hero :P

---

### Post by brammert on 2010-05-11
Hej

on my laptop, zaphod's method worked, but for my girlfriend it didn't. I can't find a mic-switch on het audio mixer either. Does somebody have an idea how to fix this?

thanks!

---

### Post by tonhou on 2010-05-16
Think the package to install is pavucontrol mentioned by dalee above (not puav control) for changing the sliders.

Tony

---

### Post by brammert on 2010-05-18
> **tonhou said:**
> Think the package to install is pavucontrol mentioned by dalee above (not puav control) for changing the sliders.

Tony
Thank you for your help, I'll try..

---

### Post by bcooperb on 2010-05-25
Thanks This worked for me, I too only had to --purge and reinstall...didn't have to do the desktop thing! 

My audio was working, but now the mic is working as well! Kudos this was an easy fix!:guitar:

---

### Post by mattweed9 on 2010-06-02
Just to let yo know, you are still helping people! I pretty much spent all morning trying to fix this one last problem, and so far so good! Now everything that is left is pretty minor.

So thanks to both zaphod777 and webified. Not sure which one fixed it, but my internal mic is now working. I haven't tried a headset yet, but my head hurts enough as it is for one day, maybe tomorrow I'll give it a go. :)

---

### Post by zaphod777 on 2010-06-02
Glad I could help this definitely gave me a headache too before I fixed it.

---

### Post by simonbanyard on 2010-06-22
Just tried 
```
apt-get install linux-backports-modules-alsa-lucid-generic
```
as per webified's post and it worked after a restart on my Vostro 1700. Now to fix the Nvidia/Plymouth issue...

---

### Post by CoolJohnB on 2010-06-23
Thank you very much, finally got Mic working!!! Needed the backports line as well, much appreciated, thanks for ALL your help.

---

### Post by CoolJohnB on 2010-06-23
I have Dell Vostro 1700 as well and am pleased to get the Mic working any idea how I can increase the volume?  Both controls are at 100% but it is very low, I can just about hear myself on Skype test call.

---

### Post by Freaky#Funga on 2011-05-03
for me worked 
[LIST=1]
[*]running alsamixer
[*]F4
[*]selecting Ext Mic with spacebar
[/LIST]

---

