---
title: "nvidia drivers curropt display at max res"
date: 2009-09-08
forum: General Help
---

### Post by DarkPontiac on 2009-09-08
Hello,

I seem to be having using the nvidia drivers that are downloaded through "Hardware Drivers."

I am using a GeForce FX5200 on the computer I am trying to run it on with a Westinghouse SK-26H730S at 1360x768@60 but for some reason it results in a "No Signal Detected" problem.

Before the driver install it works fine at 1366x768@60 which is odd, even trying 1366x768@60 with the nvidia drivers result in "No Signal Detect" problem. The thing is the signal is there because a garbled screen is presented before "Detecting Signal" and then no signal.

This leads me to believe something is wrong with the nvidia drivers itself. Either version on there (the older or newer) do the same except the older will display a lower res (1024x768 ) but upon selecting 1360x768 does the same. It will display 1280x800 though, but is stretched.

I'm doing this through VGA and windows has no problems at all displaying 1360x768@60 or 1366x768@60 so thats whats odd about all this.

I've done plenty of searching and trying different things within xorg.conf with no win..

Is there anything at all I can do to make this work? Reason I want to use nvidia drivers is to have 3D graphics support to run IMVU in wine and other 3D apps.

Thanks

---

### Post by CatKiller on 2009-09-08
> **DarkPontiac said:**
>  Before the driver install it works fine at 1366x768@60 which is odd, even trying 1366x768@60 with the nvidia drivers result in "No Signal Detect" problem. The thing is the signal is there because a garbled screen is presented before "Detecting Signal" and then no signal.

Are you sure you're picking a 60 Hz refresh rate? The nVidia driver (deliberately) misreports the refresh rate to the usual tools. Using nVidia's own tool (System &#8594; Administration &#8594; NVIDIA X Server Settings, or **nvidia-settings** from the command line) reports the correct refresh rate, though.

The symptoms you describe do sound like an incorrect refresh rate.

---

### Post by DarkPontiac on 2009-09-09
> **CatKiller said:**
> Are you sure you're picking a 60 Hz refresh rate? The nVidia driver (deliberately) misreports the refresh rate to the usual tools. Using nVidia's own tool (System &#8594; Administration &#8594; NVIDIA X Server Settings, or **nvidia-settings** from the command line) reports the correct refresh rate, though.

The symptoms you describe do sound like an incorrect refresh rate.

I've tried through there selecting 1360x768 and 60Hz but does the same... (actually in nvidia-settings 1360x768 is the max when the tv can do 1366x768 max...)

Its just weird because it works fine without nvidia drivers installed (1366x768@60hz) but with it installed this problem happens.

But either way I tried the nvidia tools when i had the older drivers installed and it defaulted into 1024x768, tried to switch it but only 1280x800 worked for the max setting..

---

