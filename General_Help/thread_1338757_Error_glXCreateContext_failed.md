---
title: "Error: glXCreateContext failed"
date: 2009-11-26
forum: General Help
---

### Post by CylnZ on 2009-11-26
So, everything was fine, I'm at the relatives for dinner, and brought my ubuntu laptop along to play games with the kids. Get it all set up, booted, and ready to play. Go upstairs to eat Thanksgiving dinner. I come back down stairs to a blank screen, not blank as in "powered off by power management" just blank. hit the space bar to log back in from the screen saver to a single desktop with no effects and no video driver. Fine, c-a-b restart X.
No change. restart the system, no change. 

desktop effects cannot be enabled.
ok.

glxinfo -l
Error: glXCreateContext failed

wine
cannot start 3d acceleration

nvidia settings looks fine, runs fine

So I google it. looks like yet another long standing issue.

So instead of playing games and having fun, I'm hunting thru the ubuntu forums looking for the fix because apparently ubuntu 9.10 cant idle an hour without falling apart. Keep in mind, this was machine that was working fine for hours at home yesterday and this morning.

Anyone else getting this problem? In search I get the usual 250 results I'll spendthe next day looking thru and eventually find the answer, but if you wonder why people dont stay with Linux, it's foolishness exactly like this that causes it. Kinda sucks to sit among 7 windows machines and 2 macs that are all playing while Linux cant manage to find it's video. I'll get to reading all the "Error: glXCreateContext failed
" threads now.

---

### Post by CylnZ on 2009-11-27
<SOLVED> Well, there are a lot of people that have had the issue and the main fix seems to be wipe the drivers totally and reinstall them. That worked for me.

---

