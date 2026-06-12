---
title: "Ubuntu 9.04 won't boot after suspend failure"
date: 2009-09-01
forum: General Help
---

### Post by StrikerMan780 on 2009-09-01
Hello, I have recently installed Ubuntu on my father's PC, due to the fact that he is bloody sick and tired with Windows' Problems. Ubuntu has been working fine for the longest time, until 2 days ago when we put the system into suspend mode. Suspend Mode didn't work properly, it just put the system into a black screen with a blinking cursor, while the system was still running at full power.

So, I forced the PC to power down since It wouldn't go anywhere, and I couldn't get it out of the broken suspend. After starting the PC up again, the ubuntu boot screen/loading bar shown up correctly, but, after loading, it just went to a black screen. No blinking cursor at all, no background sound, no response, nothing. There have been no updates recently of the Video drivers, so I highly doubt that is the problem, besides, it'd give me an X.Org error. I can't get the system past this black screen whatsoever, no matter how many times I reboot the PC.

Any ideas what might be going on, and how I might fix this?

---

### Post by gwydionwaters on 2009-09-18
bump

i have the same issue, only on ppc and i get the cursor before anything starts to initialize, after yaboot.. i can boot rescue mode from my old ibex cd ..

---

### Post by Thy_king on 2009-09-18
I had the same problem about 3-4 weeks ago.
What i did to fix it was restart the computer, but use grub, to load the "safe mode of ubuntu, i forget the exact name but i didn't use the generic version, just the previous one. once you let it load, do a proper shutdown of the system and let it reload ubuntu like it normally does.
This trick worked for me the first try.

---

### Post by gwydionwaters on 2009-09-18
thanks for the idea, i'll try that. i just need to find out how lol

---

