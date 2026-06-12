---
title: "GeForce 6200 Will Not Do Anti-aliasing"
date: 2009-09-27
forum: General Help
---

### Post by Lauxmonster on 2009-09-27
I just upgraded my computer from old onboard graphics (Intel 845G) to a Nvidia GeForce 6200 AGP card. I installed the drivers via the Hardware Drivers in the Main Menu.

Everything works except I cannot get any application to AA (Anti-alias). I have tried several programs, and many games. I played with somethings in the Nvidia X Server menu like forcing AA in all applications that can use it.

So What do I do to fix this? I am pretty new to Ubuntu and I am thinking there might be an obvious fix or a pretty easy one to this?

Thanks.

My Specs:

Pentium 4 Northwood @ 2.4GHz
1.25 GB DDR1 @ 266 MHz
Nvidia GeForce 6200
Ubuntu "Jaunty" 9.04

---

### Post by tgalati4 on 2009-09-27
Other than video memory, I'm not sure a 6200 is much of an upgrade from an 845G video chipset.

What type of display?  LCD? or CRT?  If LCD, are you driving it to it's native resolution?

Does AA show up when you run:

nvidia-settings

---

### Post by Lauxmonster on 2009-09-27
Oh a 6200 is a great deal better than a 845G Onboard chip. Just to let you know. :P. 

My monitor is a 19" Acer widescreen with its max resolution at 1440 x 900 at which it is currently set. 

Everything works great, especially Compiz Fusion. 

When I get back home, I'll check the Nvidia settings through Terminal. 

Thanks.

---

### Post by Lauxmonster on 2009-09-28
So any ideas? I tried the "nvidia- settings" and realized it was just the command to get to the Linux Nvidia Control Panel.

So, I am lost.  I installed a game called TrackMania Nations Forver, and in the Configure options, in the Anti-aliasing menu it says

- 2 samples (N/A)
- 4 samples (N/A)
- 6 samples (N/A)
- 8 samples (N/A)

I don't know why its "not available".

Thanks.

---

### Post by CatKiller on 2009-09-28
> **Lauxmonster said:**
>  I don't know why its "not available".

Nor do I. But the anti-aliasing settings in nvidia-settings will over-ride whatever the software says anyway; the anti-aliasing gets done by the driver and the game has no idea that it's being applied at all.

---

### Post by tgalati4 on 2009-09-28
Just to check, try setting your resolution to something standard like 1024x768@60 Hz and see if anti-alias is available.  Of course, it will look like crap since it is not the native resolution of the widescreen display, but it may be a limitation of the driver.

Or a bug.

I was mistaken.  I have an Intel 945 chipset and a pci nvidia 6200 card and they seem comparable.  Not sure how it compares to the 845G.

---

### Post by Lauxmonster on 2009-09-29
Still no luck. I really don't use AA on anything because my system is old as it is and adding AA to the issue doesn't help. Maybe a driver bug or something to do with chipset communication, like you said.

Thanks for everything tho.

---

### Post by snowstorm167 on 2009-11-04
I am running a geforce 6200 and play online game that will not load the high def version   I have the geforce 6200 agp 256mb  2.5 gig of ram pentuim 4ht ubuntu x64 latest

there seams to be something missing in the 64 bit drivers that is preventing the higher end from working

---

### Post by edin9 on 2009-11-04
> **snowstorm167 said:**
> I am running a geforce 6200 and play online game that will not load the high def version   I have the geforce 6200 agp 256mb  2.5 gig of ram pentuim 4ht ubuntu x64 latest

there seams to be something missing in the 64 bit drivers that is preventing the higher end from working

Game? Resolution?

---

