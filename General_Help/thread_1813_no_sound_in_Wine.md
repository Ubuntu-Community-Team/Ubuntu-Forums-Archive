---
title: "no sound in Wine"
date: 2004-10-23
forum: General Help
---

### Post by mailmesuf on 2004-10-23
I've installed Wine from the debian resources and it runs fine except there is no audio. I have audio in my system which is connected to /dev/dsp. I'm not running the esound/esd deamon mentioned in various wine forums so i can't figure it out. Wine is configured to use the standard OSS driver.

I've upgraded from Ubuntu preview.
Wine is at version 20040716
lspci gives me: Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)

Hope someone can help me out or point me in the right direction.

---

### Post by mailmesuf on 2004-10-23
I guess i'll answer my own question after fiddling with the wine config file located at ~/.wine/config.

uncomment the following options:

"Drivers" = "wineoss.drv"
"HardwareAcceleration" = "Emulation"
"DefaultPlayback" = "0" ; use first device (/dev/dsp) //if your sound device is located at /dev/dsp

Now the old Unreal Tournament and Sof2 works with sound.

---

### Post by Arawak on 2006-10-13
Well i got the same audio and same problem 
I fixed it by going to audio next to tab and turning pc speaker on and it suddenly worked ](*,) ... if that doesnt work i can probably help you other ways too.

Edit
Aslo alsa sems to work with full accel with emulation checkbox with wine builtin dsound..

somtimes without emu checkbox for me.

---

