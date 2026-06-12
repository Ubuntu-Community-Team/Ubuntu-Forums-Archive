---
title: "Hot idle NVIDIA GPU (over 70C) on Lucid compared to Karmic"
date: 2010-05-07
forum: General Help
---

### Post by scotty64 on 2010-05-07
I notice that the NVIDIA GPU on my Dell XPS M1330 gets much hotter under Lucid than with Karmic (or Windows).
While the temperature monitor in the "nvidia x server settings" showed between 50 - 60 degrees under Karmic I get readings above 70 degrees with Lucid and the fan is permanently on. I have no GPU intensive applications running.

---

### Post by dino99 on 2010-05-07
are fans working well ? maybe to dusty ;)

---

### Post by Midav on 2010-05-07
In my XPS 61C now. Used latest proprietary driver.

---

### Post by scotty64 on 2010-05-07
> **dino99 said:**
> are fans working well ? maybe to dusty ;)
Fans work well.

---

### Post by scotty64 on 2010-05-24
I think I found the source of the problem: In the Dell XPS M1330 both the GPU and the CPU sit on the same heatpipe (and probably heat each other) and I noticed that the higher GPU temperatures went along with higher CPU temperatures. I know there are mods out there to improve the cooling of this particular notebook - maybe I try one of those.

---

### Post by cascade9 on 2010-05-24
From what I've seen here, the newer 195.xx series nVidia drivers seem to use more power, and therefore create more heat, than the older 190.xx/185.xx drivers. You could try to use the older drivers...no idea how much of a pain that will be though.

---

### Post by schmandr on 2010-07-09
I observed the same, since I installed Lucid, the Nvidia GPU gets much hotter than with Karmic (both Kubuntu). I really don't touch my computer longer than necessary as it gets uncomfortably hot.

How do you mean these version numbers? The version offered by the "Hardware Drivers" (proprietary) installation Application is 173, so is it older than 195, 190 and 185, or do they just use different version numbering systems?

---

### Post by philinux on 2010-07-09
> **schmandr said:**
> I observed the same, since I installed Lucid, the Nvidia GPU gets much hotter than with Karmic (both Kubuntu). I really don't touch my computer longer than necessary as it gets uncomfortably hot.

How do you mean these version numbers? The version offered by the "Hardware Drivers" (proprietary) installation Application is 173, so is it older than 195, 190 and 185, or do they just use different version numbering systems?

They are in number order from oldest to latest.

Use the recommended version which should be shown as "Version Current".

---

