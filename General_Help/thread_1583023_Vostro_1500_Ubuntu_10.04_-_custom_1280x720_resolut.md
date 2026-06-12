---
title: "Vostro 1500 Ubuntu 10.04 - custom 1280x720 resolution?"
date: 2010-09-27
forum: General Help
---

### Post by JesperSP on 2010-09-27
Hi everyone,

I'm trying to make some HD video tutorials on youtube and therefore I would like to configure my screen so it is precisely the resolution used on HD Youtube 1280x720. My laptop has a 1680x1050 resolution, and I can also set it to 1440x900 and 1360x768, but no there is no 1280x720.

So far I have used a workaround consisting of selecting the 960x720 resolution and then having an extended desktop of 1280x720, but this means that I have to scroll around on the screen during the recording, which is seriously annoying.

I have tried the old guide in the [previous thread about custom resolutions]("http://ubuntuforums.org/showthread.php?t=1462350&highlight=custom+resolution") but when i type in the 

```
xrandr -addmode default 1280_720_60.00 --mode 1280x720_60.00
```

All I get is the error message

xrandr: Configure crtc 0 failed.

I have a Nvidia 8600M graphics card, and I'm using the proprietary driver.

Any suggestions?

Cheers,
Jesper

---

