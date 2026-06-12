---
title: "nVIDIA driver?"
date: 2010-12-26
forum: General Help
---

### Post by Maximillian_Thermidor_IV on 2010-12-26
Hi, so I'm completely new to any and all linux systems, just downloaded ubuntu 10.04 last night. While running it I noticed that my battery life was significantly less than what is was before. I had a 64-bit install of windows seven, in which I got about an hour and a half of battery life (I have a bad battery) whereas now I only get about half an hour unplugged with 64-bit 10.04. I did some looking into it and found that while generally win7 has better battery life than ubu, using an nVIDIA driver would help. I was wondering if anyone could verify this, where and how to install, and whether or not my current hardware is capable of it; Hp g61, 320gb hard drive, AMD Sempron m120 2.1ghz processor, ATI Radeon DH 4200 Graphics, 3gb ram.  Any help would be greatly appreciated

---

### Post by noah++ on 2010-12-26
What's your source for that information? I can imagine that using a proprietary video driver (i.e. one from the manufacturer) as opposed to an open source one (from the Linux developers) might optimize for video card power a little, though it's hardly the first thing that comes to my mind for overall power savings.

Whatever you read, when it said that using an Nvidia driver might help, it probably meant using a proprietary Nvidia driver would help as opposed to using the open source one that's the default in Ubuntu. You've told us you're using an ATI card though. ATI and Nvidia are competing video card manufacturers. So you'd want an ATI driver. (Or maybe it meant Nvidia cards use less power than ATI cards of the same caliber? I don't know.)

---

### Post by Maximillian_Thermidor_IV on 2010-12-26
Hm, well that being said I'm currently using the ATI/AMD Proprietary FGLRX Graphics driver, so I suppose I'm set for my driver then. Since that's not really an issue anymore I guess my question should be "what ways should i optimize power usage?". Thank you for the info

---

### Post by davidmohammed on 2010-12-26
some community info [here]("https://help.ubuntu.com/community/PowerManagement/ReducedPower") - with a useful link to lesswatts.

---

