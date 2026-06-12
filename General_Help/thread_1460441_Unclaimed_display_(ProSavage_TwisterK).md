---
title: "Unclaimed display (ProSavage TwisterK)"
date: 2010-04-22
forum: General Help
---

### Post by ciaopaulo on 2010-04-22
Hi,

While trying to get normal visual effects working on this oldish laptop I notticed the following:

```
paul@paul-laptop:~$ sudo lshw -C display
[sudo] password for paul: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK)
       vendor: S3 Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 bus_master cap_list
       configuration: latency=64 maxlatency=255 mingnt=4
       resources: memory:e0000000-e007ffff memory:90000000-97ffffff(prefetchable) memory:98000000-9800ffff(prefetchable)

```How do I make it "claimed"?


I can also see that xserver-xorg-video-savage is installed

And...
> paul@paul-laptop:~$ glxgears...will also show pretty gears


Sorry still a bit noob with Ubuntu/Linux!

---

### Post by ciaopaulo on 2010-04-25
Obligatory bump?!

---

### Post by ciaopaulo on 2010-05-03
Let's park this one up as "display will never be properly claimed".

---

