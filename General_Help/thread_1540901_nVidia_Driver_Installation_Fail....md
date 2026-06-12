---
title: "nVidia Driver Installation Fail..."
date: 2010-07-28
forum: General Help
---

### Post by ezscany on 2010-07-28
Ok guys, so I have a problem with installing my drivers. Everything I do seems to fail for some reason...

First of all, let me post my pc config:

Motherboard: nForce 750i
CPU: Intel Core 2 Quad Q6600 @ Default 2.4 GHz
GPU: 2 x nVidia 9800 GT (the 512 GDDR3 models, not the 1 GB ones)
Running: Ubuntu Lucid Lynx (10.04) 64-Bit

I'm not a newbie to Ubuntu and Linux as a whole, but I'm not that pro either. Maybe semi-newb is the right way to call myself. My only past experience with linux was using Karmic for a couple of months. So, yes, I do know the basics quite well. But it was the same situation back then with the drivers. Everything fails. I tried installing the regular way by downloading the drivers from the official site, shutting down gdm (of course, after entering the Command Line mode with Ctrl-Alt-F1), installing and starting up gdm again (oh and yes I did select the option to reconfigure xorg.conf automatically). Didn't work. Tried the propriety drivers. Didn't work as well. Tried the way with the Synaptic Package Manager. That one failed too. So basically, every way that I know leads to the same result - fail. After the restart (or just starting up gdm) it gives me that X has crashed (or can't start). I tried selecting the Reconfigure option but that didn't work. Again it brings me to the same screen. The only option is the Restart X option (I guess with the default config), but if I choose that it brings me back at 800x600 with no option of higher resolution (my native is 1680x1050). Now, If I try touching something around the drivers it gives me that I do not appear to be running a valid config and when I try to turn off the gdm it gives me some sort of an error. I've also tried running nvidia-xconfig while in gdm, but the same thing happens as mentioned above after I restart. Nothing seems to work...

I'm with a completely fresh install at the moment. Haven't even installed the updates. Can you guys help me in some way ? :D

---

### Post by jesseafrantz on 2010-07-28
> **ezscany said:**
> Ok guys, so I have a problem with installing my drivers. Everything I do seems to fail for some reason...

First of all, let me post my pc config:

Motherboard: nForce 750i
CPU: Intel Core 2 Quad Q6600 @ Default 2.4 GHz
GPU: 2 x nVidia 9800 GT (the 512 GDDR3 models, not the 1 GB ones)
Running: Ubuntu Lucid Lynx (10.04) 64-Bit

I'm not a newbie to Ubuntu and Linux as a whole, but I'm not that pro either. Maybe semi-newb is the right way to call myself. My only past experience with linux was using Karmic for a couple of months. So, yes, I do know the basics quite well. But it was the same situation back then with the drivers. Everything fails. I tried installing the regular way by downloading the drivers from the official site, shutting down gdm (of course, after entering the Command Line mode with Ctrl-Alt-F1), installing and starting up gdm again (oh and yes I did select the option to reconfigure xorg.conf automatically). Didn't work. Tried the propriety drivers. Didn't work as well. Tried the way with the Synaptic Package Manager. That one failed too. So basically, every way that I know leads to the same result - fail. After the restart (or just starting up gdm) it gives me that X has crashed (or can't start). I tried selecting the Reconfigure option but that didn't work. Again it brings me to the same screen. The only option is the Restart X option (I guess with the default config), but if I choose that it brings me back at 800x600 with no option of higher resolution (my native is 1680x1050). Now, If I try touching something around the drivers it gives me that I do not appear to be running a valid config and when I try to turn off the gdm it gives me some sort of an error. I've also tried running nvidia-xconfig while in gdm, but the same thing happens as mentioned above after I restart. Nothing seems to work...

I'm with a completely fresh install at the moment. Haven't even installed the updates. Can you guys help me in some way ? :D

I am having a similar problem, I have an on-board nVidia graphics driver and 64-bit and I am a semi-newb, it prompted me for a driver install and looked like it installed and it said enabled, but is not. Wtf

---

