---
title: "100 hertz"
date: 2010-03-26
forum: General Help
---

### Post by dioxip on 2010-03-26
Hello!

I've been trying for the past hour to get my monitor to run 100 hertz in 800x600 resolution. I can get my monitor to run at 100 hertz on the desktop in 800x600, but I want to use 1600x1200 there. It's only in quake-live and other games which I run in that resolution I want it to change to that refresh rate.

Im using a nvidia card geforce 7900 GS and I have turned off "Sync to v-blank" in the configuration menu.

I've looked into the xorg.config but I dont know what to change in there, so was afraid to ruin something.

Got this result when I ran gtf
```
klim@klim-desktop:~$ gtf 800 600 100

  # 800x600 @ 100.00 Hz (GTF) hsync: 63.60 kHz; pclk: 68.18 MHz
  Modeline "800x600_100.00"  68.18  800 848 936 1072  600 601 604 636  -HSync +Vsync

```

Hope anyone can help me with this problem :)

Regards
dioxip

---

