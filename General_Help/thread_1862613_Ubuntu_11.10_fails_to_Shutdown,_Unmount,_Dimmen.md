---
title: "Ubuntu 11.10 fails to Shutdown, Unmount, Dimmen"
date: 2011-10-16
forum: General Help
---

### Post by sid1907 on 2011-10-16
Hey,

I'm new to the whole Linux world and wanted some help from you guys.

Attached is a screenshot of the screen that pops up everytime I try to shutdown or restart Ubuntu. The screen just stays and then I'm forced to hold down the power button to shutdown.

I have no clue why this is happening. I had recently installed a few new programs like the "Start-up Manager" and the "pysdm" (for auto mounting drives).

Any help would be great! Thanks!

Also, another issue was that i did manage to mount the drive I wanted at startup but there are other drives which i don't want mounted on startup but show each time I restart. I have tried unmounting it from pysdm but it still shows.

My last issue is that every time I restart my system, my brightness setting goes all the way to 100%. I have changed that to 0% in the screen app but it still heads back to 100% on start-up.

Appreciate any help! Thanks again!

[ATTACH]204590[/ATTACH]

---

### Post by crjackson on 2011-10-17
I've noticed that this version is very picky after installing some packages. Mine did the same thing several times today.

Just open a terminal session and enter:
```
sudo shutdown -P now
```

That should force it to shutdown without having to use the power button and risking data loss.

It works for me... Ubuntu is kind of on the buggy side right now but I'm sure these annoyances will be addressed soon.

---

