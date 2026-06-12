---
title: "Ubuntu 11.10 Constant Stuttering"
date: 2012-04-13
forum: General Help
---

### Post by Fluteamahoot on 2012-04-13
Semi-New install of standard Ubuntu 11.10 64bit on Dell XPS M1330 with 1 gig of ram. After awhile, a slight, but constant stuttering happens about once every second. This is a full stutter, Mouse, Sound, video, everything, for about a tenth of a second. You can imagine that this gets slightly annoying after awhile. Present even when system is idling. Seems to have start since recent install of gnome 3. Is there any way to solve without nuking gnome 3 permanently, kinda like it. Running htop shows that even when idle, ram usage is kinda high, around 70%. I can't rollback this week, as the wifi is REALLY flakey, and I don't want to do more damage to the system.
If you need any more specs or info, just pm me or post here
Computer info:
Kernal:
Linux 3.0.0-17-generic x86_64

General Specs:
this page contains all of the specs for the M1330 except the Ram is 1GB total of 2 512MB sticks.
[http://reviews.cnet.com/laptops/dell-xps-m1330/4507-3121_7-32465545.html]("http://reviews.cnet.com/laptops/dell-xps-m1330/4507-3121_7-32465545.html")

Thanks in advance!


Edit:
Made a video capturing the stutter in action, sorry i can't screen cap, as the laptop is to low end for that.
[http://www.youtube.com/watch?v=0vpPGCPfaLU]("http://www.youtube.com/watch?v=0vpPGCPfaLU")

---

### Post by QIII on 2012-04-13
What does htop say is consuming the memory?

Even my Kubuntu doesn't consume more than 700MB at idle.

---

### Post by Fluteamahoot on 2012-04-13
Htop say gnome-shell on a fresh boot.

---

### Post by QIII on 2012-04-14
Gnome shell is consuming roughly 70% of your memory at idle on startup?

---

### Post by Fluteamahoot on 2012-04-14
It's not taking up all of the 70% but is the majority stakeholder. Other Miscellaneous tasks are also in there.

Also, just found out that laptop has 128mb of ram dedicated elsewhere, so 70% is really around 650mb used. little more normal considering windows 7 runs around 600mb on my desktop. Also tried some other WMs(LXDE, Gnome classic, AwesomeWM), but the stuttering is still present :mad:. Gnome 3 is also crashing every once in a while, maybe related. I fly home tomorrow so I will try nuking it and trying again. Maybe just a bad egg.

---

### Post by Fluteamahoot on 2012-04-15
Quick update- Arrived home today, turned on the laptop, and the stutter was gone! Not a trace of it! HTOP also reports that it is idling around 300mb, a much more reasonable number, you think? I don't know if it was a fluke, or that moronic wifi point I was using. There is only two differences that I can think of between here and there. One being that crappy hotel wifi that would deauthenticate me every several minutes. The other being the climate.

---

### Post by InnerBushman on 2012-08-04
You rebooted the laptop when the stuttering started? It helps for me tho i still don't know what is causing it :(

---

