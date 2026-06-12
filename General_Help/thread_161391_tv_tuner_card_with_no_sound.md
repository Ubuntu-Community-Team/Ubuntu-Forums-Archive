---
title: "tv tuner card with no sound"
date: 2006-04-16
forum: General Help
---

### Post by bdmp on 2006-04-16
I am installing a kworld pvr 7130 tv tuner card. The card has "ntsc" checked on the card. I got the video working but there is no sound. I am not sure what is causing it but here is a bit of what I have done and learned:

First here is some info on my card:
[http://paste.ubuntu-nl.org/12376](http://paste.ubuntu-nl.org/12376)

Here is what I did to get the video to work:
 ```
 sudo modprobe saa7134 card=3 tuner=2

```
 When I was trying to fix the sound I tried many different numbers for "card=". Basically any number seems to be fine except 5. For the "tuner=" ntsc is 2 and the card has "ntsc" checked on the front and I live in Japan which uses "ntsc" or "ntsc-jp" (I am not sure of the difference of those two).

dmesg says
```
31.
      [4296329.640000] tuner 0-0060: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
``` which is good so we know that "tuner=2" for NTSC, right?

The strange thing about this is that it says
 ```
 28.
      [4296329.455000] saa7130[0]: subsystem: 1131:0000, board: SKNet Monster TV [card=5,insmod option]
``` this is strange because if I change "card=5" it does not work. So maybe that is incorrect information?

Here is my full dmesg output:
[http://kubuntu.pastebin.com/663221](http://kubuntu.pastebin.com/663221)

Ok, now here is some info I have found on the net:

this page says something that I think is useful, and I tried to do it but I can't get it to work so maybe I am misunderstanding. Here it is:
[http://www.wlug.org.nz/TvTunerCards](http://www.wlug.org.nz/TvTunerCards)
```
Philips SAA713x

A newer chip is made by Philips. The Lifeview Fly Video 2000 and 3000 boards sold at DSE in New Zealand are based on the saa7130 chip (which uses the same driver as the saa7134 chip).

Note that this card also has a RadioTuner in it - see that page for setup hints.

Support is in the mainstream 2.6 kernel. If you use a 2.4 series kernel you will need to download drivers and a few small kernel patches from [link]http://bytesex.org/saa7134/. You will need to be using kernel 2.4.20 or later to apply these patches - the kernel patches use V4L (Video4Linux) version 2, while the 2.4 series kernels use version 1).

You still need to configure I2C support in the kernel as for BT8x8 above, as well as making a module for saa7134 ("Device Drivers -> Multimedia devices -> Video For Linux -> Philips SAA7134 support"). If you can "modprobe saa7134" then your kernel already has this module. IN 2.6.16, extra sound support has been split off into additional modules, saa7134-alsa and (apparently) saa7134-oss. You don't need these to just watch TV. See the sound section below.

Here a some gotchas I noticed (for the New Zealand version of this board, at least):

   1. I needed to add "oss=1" as a option for the saa7134 module to get any sound. I guess it was defaulting to alsa, but this option wasn't mentioned anywhere - I found it accidentally when doing modinfo(8).
   2. The default tuner type for the card was wrong. In New Zealand we use PAL BG (or compatible), and it was defaulting to some other tuner type which meant I could pick up UHF but not VHF channels. (See the notes below about tuner type).

Here is the relevant snippet from my /etc/modules.conf (for 2.4 kernels, or /etc/modprobe.d/tv for 2.6 kernels):

 # for /video0 and vbi0 devices...
 alias char-major-81-0   saa7134
 # card=3 => flyvideo2000
 # tuner=5 for PAL_BG
 # oss=1
 options saa7134 card=3 tuner=5

If you find you get video but no sound the following command may be useful as some tv applications don't unmute this card properly (ie mythtv).

assuming your V4L device is /dev/video0

/usr/bin/v4lctl -c /dev/video0 volume mute off

```

Here is a page with someone trying to install my card on kubuntu. One major difference is the "tuner=" setting. Mine is NTSC and his is PAL or something. He used "card=3 tuner=5" so I triedn changing the 5 for my NTSC to 2, so I did "card=3 tuner=2" but even after that I am having the same "no sound" problem that he was posting about in the first place. Here it is:
[http://www.flexbeta.net/forums/lofiversion/index.php/t7604.html](http://www.flexbeta.net/forums/lofiversion/index.php/t7604.html)

So I am about to buy a tv if this doesn't work soon. Save me 10000 yen and tell me how to fix this please :)

---

### Post by bdmp on 2006-04-17
I am an idiot. I didn't see the audio plug on the card.

But there are these kinda annoying lines in the screen, from electricity or something. How do I get rid of them?

And xawtv says "stick you settings in the config file ($HOME/.xawtv)" but what exactly do I put in it?

---

