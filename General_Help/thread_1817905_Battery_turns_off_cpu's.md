---
title: "Battery turns off cpu's"
date: 2011-08-03
forum: General Help
---

### Post by didgest on 2011-08-03
I have the intel N570 cpu. When i have the ac cord plugged in all 4 cpu's are online (cpu0, cpu1, cpu2, cpu3). As soon as i take the ac cord out cpu1,2,3 go offline. If I put the ac cord back in they come back online, if i turn the netbook off and start it up with out the ac cord, only cpu0 is online (cpu1, cpu2 and cpu3 are offline).

I know this is not a hardware issue cause if I boot into windows when the ac cord is not in, all 4 cpu's are online.

In Ubuntu when I do have the ac cord unplugged I can go to 

/sys/devices/system/cpu

then open a cpu folder, eg cpu1 and change the online file from a 0 to a 1. this will turn that cpu online. i can do this for the other cpu's. But as soon as i restart the netbook with no ac cord only cpu0 is online.

Why does this happen? Why is it when ever I am not using the ac power it turns off cpu1, cpu2 and cpu3? How do I stop this from happening?

---

### Post by LowSky on 2011-08-03
you only have 2 cores. the cores are then hyper-threaded with then makes it look like 4.

The processor speeds down on battery and will only use the other cores when needed. Linux only reads the cores being used. so it will only shows the used core.

---

