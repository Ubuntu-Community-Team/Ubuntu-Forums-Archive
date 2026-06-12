---
title: "1080p playback"
date: 2011-03-04
forum: General Help
---

### Post by unbuntunewb on 2011-03-04
Hello,

My computer does not do 1080p well at all. For about ten minutes it plays ok then it gets glitchy and the audio does not match the video. it can handle 720 with minimal lagging. What types of upgrades do I need to get a smooth video experience?

I think I have a amd 2800 with 2 gigs of ram

---

### Post by WorMzy on 2011-03-04
Well, I can run 1920x1080 videos perfectly with my Intel E8500 + nVidia GeForce 8800GTX, I'm not sure what that translates as in the AMD/ATi world, but perhaps you can use that as a baseline.

I have 4GB of high quality RAM, although that doesn't seem to make much difference (watching a 1920x1080 video just uses an additional 2-3% RAM).

I use SMplayer as my media player, which may be a factor. You could try increasing the cache size if you're playing files from removable media, that may have a beneficial effect on playback, although it may also have a negative effect on seeking.

---

### Post by davidmohammed on 2011-03-04
> **unbuntunewb said:**
> Hello,

My computer does not do 1080p well at all. For about ten minutes it plays ok then it gets glitchy and the audio does not match the video. it can handle 720 with minimal lagging. What types of upgrades do I need to get a smooth video experience?

I think I have a amd 2800 with 2 gigs of ram

what is your graphics card? 

type in a terminal

sudo lspci | grep VGA

Have you installed any graphics drivers recommended in Administration - Hardware Drivers?

---

### Post by unbuntunewb on 2011-03-06
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)

---

### Post by davidmohammed on 2011-03-06
...

Have you installed any graphics drivers recommended in Administration - Hardware Drivers?

As an aside - that is an integrated graphics card correct?

It is not designed as far as I understand for HD playback - you'll need to purchase a better card for HD.

---

### Post by cascade9 on 2011-03-06
> **unbuntunewb said:**
> Hello,

My computer does not do 1080p well at all. For about ten minutes it plays ok then it gets glitchy and the audio does not match the video. it can handle 720 with minimal lagging. What types of upgrades do I need to get a smooth video experience?

I think I have a amd 2800 with 2 gigs of ram

2800+ hasnt really got enough power to decode 1080p. 

If you have PCIe slot, a 8XXX or higher nVidia card (not 8800GTX, 8800 Ultra or 8800 GTS G80) and VDPAU should make it play 1080p just fine. 

If its an AGP GeForce 6150SE nForce 430...then maybe a CPU upgrade (depending on what CPUs you can use, and what you can find)

---

### Post by ShakeyJake on 2011-03-06
To really watch HD videos properly, you'll need a card from [this]("http://en.wikipedia.org/wiki/Nvidia_PureVideo#Table_of_PureVideo_.28HD.29_GPUs") list. If it's just for HD video and nothing else, might I recommend a passive Geforce 210? Totally silent, more than enough power and very, very cheap.

---

### Post by flipper T on 2011-03-06
i experienced glitchy playback in hd videos

i alleviated this by messing with cpu scaling and setting it to the max possible

i may be wrong in assuming that this had an affect, but....well it did

easy way to set scaling preferences is to use the panel applet "cpu frequency scaling monitor"

you will need to add an applet for each of your cpu's cores and alter preferences accordingly

...maybe worth a try


ps ... if you can ignore the increase in fan noise

---

