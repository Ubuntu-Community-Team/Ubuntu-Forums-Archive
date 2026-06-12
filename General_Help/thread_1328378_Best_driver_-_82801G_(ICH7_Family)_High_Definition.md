---
title: "Best driver? - 82801G (ICH7 Family) High Definition Audio Controller"
date: 2009-11-16
forum: General Help
---

### Post by Poyntz on 2009-11-16
Hi folks,

Here's my audio setup:
> description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:30 memory:d2400000-d2403fff

```
cat /proc/asound/card0/codec#* | grep Codec
```
returns
> Codec: Conexant CX20551 (Waikiki)

Two issues:
1. The sound quality is crap
2. The mic doesn't work

Basically, I have no idea what driver I should be downloading or how I can update it. When I was using Hardy the sound quality was fine and the microphone worked. It's never been as good on Intrepid, Jaunty and Karmic and I've never been able to get the microphone working on these three distros. 

I'm guessing it's a driver issue but I have no idea. If it is please tell me what driver I should be downloading and how I can get the latest.

Cheers.

Chris

---

### Post by Poyntz on 2009-11-17
Ok. I've gone a step ahead.

Now my sound quality is better and my microphone records!

The down is that even if I set my mic and capture levels to the top level it still records extremely quiety :/.

If anyone can help me fix this that would be great.

Basically the mic record level is so low that it's practically useless anyway...

--------------------------

(So what I've done to get them working)
1. I removed the old linux-headers (anything before 2.6.31-14) [only do this if you're on Karmic]
2. I installed the latest alsa driver from [http://www.alsa-project.org](http://www.alsa-project.org) (alsa-driver-1.0.21)
3. I randomly picked and chose from the other source packages displayed
[LIST] 
[*] alsa-lib-1.0.21a
[*] alsa-utils-1.0.21
[*] alsa-tools-1.0.21
[*] alsa-firmware-1.0.20
[*] alsa-plugins-1.0.21
[/LIST]
untarred them and compiled:
eg (for the first one), 
```
tar -jxvf alsa-driver-1.0.21.tar.bz2 && 
cd alsa-driver-1.0.21/ && 
./configure --with-cards=hda-intel && 
make && 
sudo checkinstall
```
4. I rebooted

---

