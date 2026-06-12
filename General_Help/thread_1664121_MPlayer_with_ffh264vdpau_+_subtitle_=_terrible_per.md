---
title: "MPlayer with ffh264vdpau + subtitle = terrible performance"
date: 2011-01-10
forum: General Help
---

### Post by veggen on 2011-01-10
I have just noticed something weird. When playing a h264 movie in MPlayer using ffh264vdpau (hardware accelerated), everything works fine until I try loading an external subtitle (.srt in my case). At that point memory usage goes through the roof and the video starts lagging severely. CPU usage is still very low.

Can someone please confirm this? I'd be very, very, grateful.

You can try with this [trailer for *The Bourne Ultimatum*](http://www.fdccdn.net/33772/trailers/divxdigest/bourne_ultimatum_trailer.zip) and [this](http://www.podnapisi.net/cyr/ppodnapisi/download/i/908292/k/153b292fa511f31c136a3e18ea712043b576cfef) subtitle (for *How to train your dragon*). Those two together, played with ffh264vdpau bring my computer to a crawl.

[DISCLAIMER]
This discussion originated [here](http://ubuntuforums.org/showthread.php?t=1663359) but evolved into a different subject completely, hence a new thread.

---

### Post by veggen on 2011-01-11
More info.
Everything is normal until the first line of the subtitle is supposed to be displayed. That's the exact moment it goes haywire.
Also, if I play it from the command line e.g.
mplayer -vo vdpau -vc ffh264vdpau -sub ~/a.srt ~/a.mp4
all is fine.
When I'm playing from SMplayer and hover over the mplayer process in System Monitor, there's no -sub switch.
All this leads me to the conclusion, SMplayer (and other MPlayer front ends, I tried others too) render subtitles differently and this difference is what causes this severe lag.
Any ideas what might be different between loading a subtitle through mplayer's -sub switch and loading through SMplayer?

---

### Post by veggen on 2011-01-11
Please... Just try it out on your machine to see it if works for you... It's a minute of your time (well, depending on your connection speed).

---

### Post by veggen on 2011-01-12
*bump*

---

### Post by veggen on 2011-01-13
105 views and noone can confirm/refute?

---

### Post by gradinaruvasile on 2011-01-13
What hardware, driver version + smplayer version do you have?

I can confirm the higher cpu usage with that trailer+sub. I have a nvidia 8200 integrated chip (+athlon II x2 3.00 ghz cpu), i use vdpau decoding that has max 10% cpu usage on h264 1080p movies. But in this case whenever the subtitle appears, i have spikes up to 50%. But the playback is smooth. 
BTW i use Debian Squeeze with smplayer 0.6.9-1 and mplayer 2:1.0~rc3++svn20100804-0.1.

---

### Post by veggen on 2011-01-13
Wow, thanks a bunch!

I'm not by my machine at the moment, but I have:
1. GPU: nVidia GeForce 8600 GT CPU: Intel C2D E4400
2. The latest proprietary nVidia driver Ubuntu offered
3. MPlayer 1.0 rc4 and SMPlayer from Ubuntu 10.10 repo

I'll edit the post for more precise info later today.

For me the CPU usage is always around 2%, but memory usage explodes (from about 50MB to over 700MB) when it starts rendering subtitles and the video lags severely at this point. This happens for every h264 1080p movie and srt subtitles.
When playing from the command line, CPU is at constant 2% and memory is always low with no lag.

Since it's acting up for you as well, I guess it can be assumed it's normal behavior.

Thanks again for trying it out! Greatly appreciated!

---

### Post by gradinaruvasile on 2011-01-13
Mplayer does the real work, i have smplayer at 1-3 % too.

I tried other hd movies but i had no difference there. Seems that this is triggered by specific circumstances. And i did not have the memory increase.
For example these:

[http://www.divx.com/en/electronics/solutions/high-definition/divx-plus-hd/video#showcase](http://www.divx.com/en/electronics/solutions/high-definition/divx-plus-hd/video#showcase)

---

### Post by HunterAtUbuntu on 2011-02-17
If you're still having this issue, try upgrading to the latest nvidia drivers with this ppa
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
For me that completely fixed the problem and then some

---

### Post by veggen on 2011-02-18
Wow, thanks! Yes, I still have this problem. Will try your solution and post the results.
Thanks again!

---

### Post by veggen on 2011-02-19
Ok, I've tried it out. The situation is now much better, but still not exactly right. Now, when the subtitle is rendered, instead of memory usage going insanely up, the CPU usage increases to little less than what it would be without the hardware acceleration.
Since that doesn't cause the severe lag, I'd say it's better than with the previous driver version. Also, I now know exactly where the problem lies - the driver. I'll keep a look on future updates, at some point it just might start working properly.

Thanks a lot for the advice HbrShred, you're great! All in all, watching HD videos **has** become much more comfortable now.

[EDIT]
Works even better with last week's updates :)

---

