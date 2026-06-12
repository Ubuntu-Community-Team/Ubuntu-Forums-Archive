---
title: "No sound through HDMI (but was working fine yesterday)"
date: 2011-12-19
forum: General Help
---

### Post by CrazzzyBudha on 2011-12-19
Dual booting Ubuntu 11.10 and Windows. Intell Integrated Graphics Controller is listed when I run: lshw -C video. Laptop: Acer Aspire Timeline X 4820T

I am trying to play Boxee on Ubuntu through my HDTV using HDMI. It was working great until yesterday, now I get sound from internal laptop speakers and video still plays fine on TV. I didn't change anything, not even running an update, when it suddenly stopped playing through TV. In sound settings my only option is internal audio analog stereo (under output). When I run ```
aplay -D plughw:0,3 /usr/share/sounds/alsa/Front_Center.wav

``` (as suggested by the Ubuntu sound trouble shooting guide) it plays through the TV, but nothing else.

I've tried a bunch of things (hopefully didn't make anything worse because of it) after reading through the forums including: 

creating /ect/asound.config with the following:
```
pcm.!default {
  type plug
  slave {
    pcm "hw:1,0" #delete the first hash for sound over analog
#    pcm "hw:1,1" #delete the first hash for sound over optical
#    pcm "hw:0,3" #delete the first hash for sound over hdmi
    rate 48000
  }
}

```
and adding this line to the end of etc/pulse/default.pa
```
#load-module module-alsa-sink device=hw:1,7
```
Any help would be much appreciated, thanks!

---

