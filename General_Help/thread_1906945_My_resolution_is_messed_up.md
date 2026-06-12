---
title: "My resolution is messed up"
date: 2012-01-10
forum: General Help
---

### Post by searchfgold6789 on 2012-01-10
Hi,
My monitor cable was a bit damaged and wouldn't show the right colors at times, so I had to buy a new VGA male-to-male cable for my LCD monitor.
I went on Amazon and they had these for like $5 - I got the cheapest one which was a "Hi-res" one, I don't know what that means though. It fits into the sockets.
However when I boot into Kubuntu or Ubuntu the display is at a very low resolution. It's at the highest possible one, so there's no way to change it. Also the GRUB menu is at a lower resolution than before, and it's a bright blue instead of a light blue.
It works fine in Windows, but it lags and is horrible ... wait, no, that was an existing problem!
EDIT: I just looked back and saw that it's an HD15 VGA cable, if that makes any difference!

ANOTHER EDIT:
When I remove the nVidia driver from use, I can get up to 1024x768, which is not the resolution I need. Then when I put it back nVidia settings says I have a CRT and I can only go up to 640x480 :(

---

### Post by searchfgold6789 on 2012-01-11
Today I tried the Ubuntu Experimental NVidia Support Drivers. I could get up to 1024x768 but that is terrible on this screen! NVidia still thinks that this screen is a CRT, perhaps that's from before when I did have a CRT monitor.

---

### Post by 2F4U on 2012-01-11
It may be a problem with the quality of the cable. This Wikipedia article suggests, that cable quality has an influence on the resolution:

[http://en.wikipedia.org/wiki/VGA_connector](http://en.wikipedia.org/wiki/VGA_connector)

---

### Post by searchfgold6789 on 2012-01-11
I read that particular article, and found that it suggests the opposite:> The same VGA cable can be used with a variety of supported VGA resolutions, ranging from 640×400px @70 Hz (24 MHz of [signal bandwidth]("http://en.wikipedia.org/wiki/Signal_bandwidth"))  to 1280×1024px @85 Hz (160 MHz) and up to 2048×1536px @85 Hz (388 MHz).  There are no standards defining the quality required for each  resolution, but higher-quality cables typically contain coaxial wiring  and insulation which make them thicker.The cables each have the same number of pins, and I know that the cable can handle the proper resolution: When I first received the cable in the mail, I didn't turn my computer off but just switched the cable out, and the color problem was fixed and everything was normal.
My problems arose when I rebooted. Now it only goes up to 640x480 because nvidia-settings is detecting the wrong type of monitor. I have tried reinstalling nvidia drivers with apt, and also from their website which caused Kubuntu to be entirely unbootable, with my monitor giving me an "out of range" error.

---

### Post by Kslawdog on 2012-01-11
Might check this out.

     [http://www.linuxquestions.org/questions/linux-newbie-8/please-tell-me-how-to-reset-my-screen-resolution-or-reinstall-ubuntu-via-the-terminal-621567/](http://www.linuxquestions.org/questions/linux-newbie-8/please-tell-me-how-to-reset-my-screen-resolution-or-reinstall-ubuntu-via-the-terminal-621567/)

---

### Post by searchfgold6789 on 2012-01-12
Thanks!!! I tried the suggestion there: 'sudo dpkg-reconfigure xserver-xorg'. Nooo luck. Well I suppose I'll try switching the monitor cable now!

---

### Post by chandan_raka on 2012-06-05
My laptops resolution got messed up. Basically in order to make my external monitor I installed nvidia-xconfig and that generated on xorg.conf file. My external monitor didnt work but my laptops resolution got messed up.

So I deleted the /etc/X11/xorg.conf file and restarted it worked.

However, in ubuntu 12 I guess they have removed default xorg.conf file.

---

