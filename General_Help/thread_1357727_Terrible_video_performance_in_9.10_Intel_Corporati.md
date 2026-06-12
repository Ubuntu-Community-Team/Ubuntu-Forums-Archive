---
title: "Terrible video performance in 9.10 Intel Corporation 82845G/GL[Brookdale-G]/GE"
date: 2009-12-17
forum: General Help
---

### Post by b4t3m4n on 2009-12-17
I have a semi old PC.  HP Pavilon a405n.  2.7 GHz Intel Celeron, 1 gig Ram and a Intel Corporation 82845G/GL[Brookdale-G]/GE video card with 64M shared video RAM.

I am running Ubuntu 9.10 standard install with all updates installed.  I have turned off all flashy desktop effects, but it is still very sluggish.

Windows render slowly, and they shear when moving them around the screen.  I tried to look at the xorg.conf for any clues but it seems like it doesn't exist anymore in 9.10, do they do some sort of auto configure now?

any help would be appreciated

---

### Post by lazychris2000 on 2009-12-17
In my experience with this specific video chipset, I have *always* had terrible performance with it, whether in windows or linux.  I would recommend picking up a cheap nvidia video card and using it instead.  Even with something as old as a Geforce 4, I have had smooth performance with desktop applications.  You could probably pick up a used card for a few dollars at a local computer shop (most likely mom and pop style ones, not the international big box chains).  Failing that, any nvidia card on the shelf should be sufficient, just grab a cheap one.  Make sure you get a PCI card (NOT PCI-express!).  Looking at the specs of your system, there are no AGP or PCI-e slots.
If anyone else has had success with this chipset, I would be most interested in knowing your secrets.

---

### Post by jruberto on 2010-02-15
I'm running Karmic on an older Dell laptop with this video chipset.  I ran XP on this machine for years before switching.  I immediately noticed the video performance was terrible on Ububtu compared to XP.  

I tried a lot of stuff that didn't make any difference but what got me a noticeable improvement in video performance was un-installing compiz altogether.  I did have visual effects set for "none" but still noticed a great performance increase after un-installing.

In Synaptic, just quick-search compiz & mark all the installed components for removal.  Hit apply, reboot, and it's much better.  Still not great, but a lot better.

Cheers,
j

---

