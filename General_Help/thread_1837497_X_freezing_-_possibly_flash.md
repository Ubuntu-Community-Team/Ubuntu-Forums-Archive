---
title: "X freezing - possibly flash?"
date: 2011-09-01
forum: General Help
---

### Post by rotten777 on 2011-09-01
Just some background... the hardware in this system has been stable for a long time. The solid state main drive and second hard drive are both less than 6 months old. I've tested all the hardware and there are no problems.

Just within the last two months I'd say the system has started to have freezes with firefox and flash. But not just a freeze where I jump into a terminal and kill a process but I'm actually freezing X and I cannot jump to any terminals to fix it. I can hear the fans crank up on the cpu so I'm sure it's something going to 100% cpu usage and looping.

I'm running an nVidia GTX 285, AMD 1100T, 16GB RAM... I use the flash-aid addon for Firefox and I have the latest version of flash. The system is up to date as far as the repo's go.

It's just some weird freezing happening way too often. 

Thanks to anyone in advance

---

### Post by lovinglinux on 2011-09-05
First make sure you get [Flash-Aid 2.2.1]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/"), since there is a bug in the current version that affects FF 6.

Then run the Wizard and try to disable the GPU validation tweak. Enable it if it doesn't solve the problem.

Also, try to clean up the fan. Most likely that flash is overheating the CPU.

I would recommend [FlashVideReplacer]("https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/") for YouTube.

---

