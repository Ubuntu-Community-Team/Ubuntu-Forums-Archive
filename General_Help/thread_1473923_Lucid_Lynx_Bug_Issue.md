---
title: "Lucid Lynx Bug Issue"
date: 2010-05-05
forum: General Help
---

### Post by cusinmex on 2010-05-05
Forum,

Lucid Lynx upgraded seemingly well and i didn't have any
problems until i came across this bug; 

I'm running Lucid on a HP Pavilion dv4-2012la laptop, and
it seems that whenever i try to adjust the power settings
somehow, the pc just shuts off immediately and restarts.

I first discovered it when i tried to adjust the brightness
setting for the screen using the {Fn} key and the {f7} key at the 
same time, but instead of lowering the brightness like it is supposed
to, it turned off immediately.

After it restarted and all, I decided to unplug the AC Power cable because the battery was done charging, and again, it turns off.

So it seems that its a Power Management bug?   :confused:


Is there a fix to this?

Thanks in advance.

---

### Post by StuartN on 2010-05-05
> **cusinmex said:**
> After it restarted and all, I decided to unplug the AC Power cable because the battery was done charging, and again, it turns off.

Since Ubuntu 9.10 I have had a problem with the laptop switching off when the power cable is plugged in ([https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/554894](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/554894)) - if I managed to plug in the powercord before the battery redlined and generated a warning, then it would recharge. If the battery warning came up, then plugging in the powercord triggered an immediate shutdown.

I haven't managed to run the battery down enough in Ubuntu 10.04 yet to test whether this bug remains, but Launchpad isn't marked complete.

---

### Post by cusinmex on 2010-05-05
In Ubuntu 9.10, everything worked fine i could plug in the cable
whenever i wanted to, and it would work perfectly and charge...

so this is sort of a surprise to me :S

---

### Post by Orlsend on 2010-05-17
Hey this is random,but how did you get the wireless to work on that model?

---

