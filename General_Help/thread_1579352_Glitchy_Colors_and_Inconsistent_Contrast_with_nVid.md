---
title: "Glitchy Colors and Inconsistent Contrast with nVidia SLI"
date: 2010-09-21
forum: General Help
---

### Post by belize1334 on 2010-09-21
Some of you may have seen my previous thread about inconsistent font contrast in Firefox. It turned out to be an issue with my nVidia proprietary drivers.

I'm currently running two GeForce 7600 GT cards on a P5n-D mobo with SLI capability.

With --sli=false the video quality is great but I'm only making use of GPU-0. If I enable SLI via sfr, afr, or auto then the fonts become inconsistent and I get color glitches. In afr the glitchyness is kind of wobbly and occurs for about a second any time the screen is shifted (like panning between desktops). In sfr mode the glitchyness is constant and only on the lower half of the screen. Both indicate to me that the second card is failing to render effectively. I tried swapping cards but it made no difference which tells me it's probably driver related and not hardware. I tried capturing screen shots but the colors seem to fix themselves as soon as I press prt-scr. I ended up with a camera pic (attached) which is low quality but gets the point across... This is in sfr and you can see that the glitchyness is exclusively on the lower half of the screen.

I also noted while playing nexuiz that I got ZERO performance gain from running in SLI mode. 

I'm currently running the nvidia-173 driver since v-96 WOULDN'T run in SLI and v-current makes the card fans run full blast all the time which is annoyingly loud. In any event, v-current showed all the same symptoms with SLI enabled.

Of course the current solution is to just disable SLI and I may just put one of the cards on ebay and be done with it. But if anybody else has had a similar issue and can offer some advice I'd really like to make this work since I've already got the hardware...

---

