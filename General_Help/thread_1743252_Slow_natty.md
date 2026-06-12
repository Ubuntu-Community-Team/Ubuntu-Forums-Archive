---
title: "Slow natty?"
date: 2011-04-29
forum: General Help
---

### Post by Red Skare on 2011-04-29
Just updated to 11.04 and was wondering does anyone else have problems with it being a little slow? When i move windows it seems real choppy and sluggish.Is there a fix for this?
I have the 64 bit version
965 phenom quad core
ATI 6870 video card

Also has anyone been able to get the animations from compiz working on this? Im having trouble with my window boarders and that unity thing on the left just disappearing whenever i do anything in compiz. I really want my desktop cube wobbly windows and burn back

---

### Post by sikander3786 on 2011-04-29
Did you install the proprietary drivers for your graphics card?

I got Wobbly windows working under Compiz so it is possible and nothing geeky there. I used ubuntu-tweak to enable those effects.

---

### Post by Red Skare on 2011-04-29
> **sikander3786 said:**
> Did you install the proprietary drivers for your graphics card?
 
I got Wobbly windows working under Compiz so it is possible and nothing geeky there. I used ubuntu-tweak to enable those effects.
 
Yes i did install the drivers from the ATI site, is unity slow and coppy on your computer?

---

### Post by sikander3786 on 2011-04-29
Not at all slow. It is working just fine as one would expect.

Install ccsm, go to OpenGL plugin and disable the 'Sync to VBlank' option. Reboot and it should work fine I hope.

For installation,

```
sudo apt-get install compizconfig-settings-manager
```

For Launching ccsm, press the Window logo button <super> and type 'compiz'. You should see it.

---

### Post by Red Skare on 2011-04-29
Thanks a ton im going to do this latter and see how it goes

---

### Post by Liam1995 on 2011-04-30
> **sikander3786 said:**
> Not at all slow. It is working just fine as one would expect.

Install ccsm, go to OpenGL plugin and disable the 'Sync to VBlank' option. Reboot and it should work fine I hope.

For installation,

```
sudo apt-get install compizconfig-settings-manager
```

For Launching ccsm, press the Window logo button <super> and type 'compiz'. You should see it.
Excellent help, worked just as expected! :D

---

### Post by Red Skare on 2011-05-01
That stuff did not work and compiz effects kept breaking ubuntu. Window boarders would dissappear or it would just not respond at all. So i removed ubuntu 11 from my computer and put 10 back on, problem solved.

---

