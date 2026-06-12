---
title: "Xorg running under &quot;root&quot; &amp; slowing performance"
date: 2009-12-17
forum: General Help
---

### Post by astrobob.tk on 2009-12-17
Hey there,

I just been working on my laptop & realized its getting slow & the performance has decreased. I opened the "System Monitor" to discover Xorg (which I don't know what it is) using between 30 to 50% of the cpu.

Could you please help :confused: ?

thx

---

### Post by lewisforlife on 2009-12-18
Xorg is your X Server for displaying graphics, desktop environment, etc... This is normally one of the top users of the CPU, 30-50% is normal.  There is nothing you can really do about it unless you want to quit using a desktop environment and just use the shell. :)

---

### Post by internalkernel on 2009-12-18
I think 30 to 50 is quite a bit for Xorg, mine idles around 5%... I've never seen it peak above 20% without some graphics intensive apps running. 

What kind of video card do you have? Did you install any 3rd party drivers for it? Through jockey maybe, I think they call them restricted drivers... 

Are you on Karmic? 

and run these commands in a terminal (Accessories --> Terminal)
```
dpkg -l |grep xserver-xorg-core
dpkg -l |grep xserver-xorg
```

The second command will probably spit out alot of results, I only want to know what the first one is... xserver-xorg

---

### Post by astrobob.tk on 2009-12-19
> **lewisforlife said:**
> Xorg is your X Server for displaying graphics, desktop environment, etc... This is normally one of the top users of the CPU, 30-50% is normal.  There is nothing you can really do about it unless you want to quit using a desktop environment and just use the shell. :)

well i realized that the performance went down & although i was only running firefox & some other other application that I usually run. It seems that vanished now. Xorg is now using between 5 & 20%.

btw, i dont know what vga or graphic card I have how could i know details about it ?

thx

---

### Post by internalkernel on 2009-12-19
try: 
```
sudo lspci -v
```

That will show you all hardware on your system, don't post all of the output - search through and find you video card...

How's Xorg running now? Is it better, in normal ranges - can you identify anything that makes is spike?

---

### Post by astrobob.tk on 2010-01-01
I suppose here is the video card:

> 01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
    Subsystem: Dell Device 2001
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 32, 

Regarding Xorg, i think things are going fine, its reaching up to %30. talking about normal ranges, is it normal for firefox to use about 150MB of memory ? what about 500 ? i was doing lots of stuff for 24 hrs lol & firefox started stopping to respond very often. after restarting my system it went down to 150.

---

