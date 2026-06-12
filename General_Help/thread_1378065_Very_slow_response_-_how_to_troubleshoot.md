---
title: "Very slow response - how to troubleshoot?"
date: 2010-01-11
forum: General Help
---

### Post by Paul Garthe on 2010-01-11
My Kubuntu installation (9.10) boots up normally and seems to run fine, other than it is very slow to respond to inputs or change screens/ applications etc.  It can take 5-10 seconds to respond to simple requests like changing from firefox to dolphin by clicking in the taskbar.  It is dual boot with XP, which also seems sluggish, but is bearable.

The computer is barely useable in Kubuntu because of the slow response.  I had 9.04 installed before, same problem.  I tried searching for drivers for the on board video, thinking that might be it, but came up empty.

- Asus P5KPL-CM motherboard
- E5200 processor
- 4 GB ram
- 300 GB ATA drive (no SATA drives)

The hardrive does not seem to be working hard during the slow down, just does not seem to register for several seconds.

Any idea what to check and how to troubleshoot this?

Thanks,
Paul

---

### Post by tgalati4 on 2010-01-11
open a terminal:

sudo apt-get install htop
htop

Pay attention to what is running when the computer slows down.

---

### Post by Paul Garthe on 2010-01-11
/usr/bin/X -br -nolisten tcp :0 vt7 -auth /var/run/xauth/A:0-nSrPP5
Stays consistently on top while running and switching tasks (when slow) at 40- 98 %CPU typically.

Second is usually kmix [kde init] at CPU% 2

Actually htop does not change at all for a few seconds while the computer "hangs" after an input to change tasks.  Right after that the CPU% on /usr/bin/X ..... goes up to 90% +.

This is quite a bit different than my other computer with 9.04 installed, which flashes many different processes accros the top including /usr/bin/X ... (but which only looks like it uses about 5 CPU%).

Paul

---

### Post by Gen2ly on 2010-01-11
Hmmm, I'm guessing this has to do with composting.  Do you have Desktop Effects enabled??  That number is way too high unless your computer/graphic card is pretty old.  Typically X for me uses 1-2% on a Core Duo.  You can go into System Settings > Desktop > Desktop Effects > Advanced and play with the settings and it might (just might) just fix it.  If not try disabling composting completely and see if that helps.

---

### Post by Paul Garthe on 2010-01-11
Compositing was already disabled.  I tried enabling it, and it got reeeaaally slow (lost kde window decorations for about 30 seconds).  Video chip is on board 3D, don't hink its that old or slow.

---

### Post by Gen2ly on 2010-01-12
Well looks like you got a bug (likely a driver issue with the X server).  Best thing I can think that you can do is: 1) Report this on the bug tracker (launchpad) and hopefully get help there, 2) Try another KDE distro which may have a newer (or older) version of X... that doesn't have your bug.  Popular KDE distributions are: OpenSuse, Mandriva...  Hmm :), can't think of any others right now.

---

### Post by Paul Garthe on 2010-01-16
Thanks for the help.  

I tried a live CD and installing Ubuntu 9.10 x64, they both worked normal speed/ fine.  I then installed Kubuntu 9.04 (could not seem to install kubuntu 9.10 again- I may have upgraded from 9.04 last time).  It gave me an option to delete 2 (sound?) drivers right after install, then seemed to work OK (htop showed only 4-6 CUP% on the usr/bin/X -br -nolisten ....), even with compositing enable.  Only problem is it seems to hang too often.  I prefer Kubuntu, but will use Ubuntu on this machine since it seems to work better with the hardware I have.  I've never tried filing a bug report, went there and it seems a little onerous, but will give it a shot when I get the time.

Paul

---

