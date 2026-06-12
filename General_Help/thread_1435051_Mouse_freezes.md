---
title: "Mouse freezes"
date: 2010-03-21
forum: General Help
---

### Post by marcfell27 on 2010-03-21
Tried the dell support forum with no replies in a week, anyone else that could point me in the right direction???

After a clean install of 9.10 the usb mouse freezes after 5.10 mins and only a restart will get it going again. Can still use the usb keyboard though. I've tried 3 different 'mice' and same prob with all.

I installed ubuntu on grandads machine after telling him how great ubuntu is. He has a dell dimension c521 amd64 with nvidia, I installed the 32bit version.

I've also tried reinstalling 8,10 with the same exact problem.... very frustrating.

---

### Post by lightspd on 2010-03-21
What kind of system are you running, peripherals?  Sounds like something is probably conflicting with it.  The only time I've seen something similar was on an old 486 system I had.  The modem and mouse were conflicting, so anytime I would dial into a BBS, my mouse wouldn't work.  Didn't really matter back then, but might be something similar conflicting with your mouse.

---

### Post by marcfell27 on 2010-03-21
not sure all the specs as the machine is at grandpa's, but I just read a post where someone had a similar prob and found that his media card readers were the problem.

So I'm going around to disconnect those and maybe upgrade the bios was another suggestion I've found....

---

### Post by lightspd on 2010-03-21
Another thing to try is next time it freezes cat /dev/input/mice, move the mouse around and see if you get any output.  You should see gibberish, if the system is seeing the mouse moving.  Are there any error messages in your logs?  One last thing to try is boot into recovery mode and see if the problem still happens.

---

