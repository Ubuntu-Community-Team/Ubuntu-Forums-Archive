---
title: "love and other bugs"
date: 2011-08-19
forum: General Help
---

### Post by htedrom on 2011-08-19
so I've just updated to 11.04 from 10.04- so far so great, but I have run in to a couple strange bugs that google doesn't seem to know much about. maybe you guys do..

1. when i press the 'up' button in a gnome terminal in xfce it takes a screenshot instead of cycling through the gnome-terminal command history- both the gnome and the compiz shortcuts have nothing to do with the 'up' button though

2. perhaps more seriously, I get pseudo random purple-ubuntu-loading screens of death. I'm not able to totally replicate yet but it seems to have something to do with switching ttys from x to terminal. when it happens i have to reboot the dm to get back into x.

just those two so far, does anyone have any ideas?

---

### Post by htedrom on 2011-08-19
OK now it's really getting frustrating. Really weird things put me to the purple screen of death, I was just now able to replicate it every time I hit enter on the password form at facebook.com and it happens every time I try switching to another tty; I'll try to come back to X and it will be purple ubuntu loading screen. When I get the purple screen both X and lightdm are still running processes, but it doesn't look like firefox or skype or any of the programs are.

I have no idea what's going on here, will update as I find other bizzare triggers for the PSOD.. last night I was convinced it was getting triggered every time I unloaded my wireless driver ath9k.

dmesg seems totally benign

```

[  379.017550] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  379.017552] cfg80211: Disabling freq 2467 MHz
[  379.017553] cfg80211: Disabling freq 2472 MHz
[  379.017555] cfg80211: Disabling freq 2484 MHz
[  379.017559] cfg80211: Regulatory domain changed to country: US
[  379.017561] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  379.017564] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  379.017566] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  379.017569] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  379.017572] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  379.017574] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  379.017577] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)

```

kernel also just updated but I was having the problem before as well

$ uname -r
2.6.38-10-generic

---

### Post by jfed on 2011-08-19
Off of a LiveCD session I had the same problem as your first, I'd like to see how this turns out.

---

### Post by jim_deadlock on 2011-08-20
I've been getting random logouts maybe once every couple of days, it happens usually when I'm entering some text in a web form, I hit enter and bang, logged out for no apparent reason. It's been happening for months ever since I bought this computer, I'm running 11.04/Unity. Seems like the same problem as you have, don't have any solution I'm afraid but will be watching this thread...

---

### Post by htedrom on 2011-08-26
Well I'm not sure if this will work for you guys too, but switching back to gdm from lightdm seems to have solved this problem for me... if you're using lightdm give it a try.

---

