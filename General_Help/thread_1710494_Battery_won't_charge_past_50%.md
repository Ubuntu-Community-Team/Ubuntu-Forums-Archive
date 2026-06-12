---
title: "Battery won't charge past 50%"
date: 2011-03-19
forum: General Help
---

### Post by SekiTimewalker on 2011-03-19
Back when I had Windows, I used Sony Care to make my battery stop charging at 50%. I did this because it supposedly extended overall battery life, and when I went someplace where I would be without my cord, I could shift that back to 100%, only keeping it at 50% when I'm at home. Now that I'm on Linux, I cannot change that, so my battery is stuck at only 50%, as there is no Sony Care program for Linux. Is there a workaround for this? It would be nice to be able to charge my battery to 100% again. Also, and I am assuming this goes hand in hand with the charging issue, it won't tell my battery percent when charging, it just says estimating. When I unplug it, it tells me that my computer will suspend very soon as the battery is critically low. Even though it is at 50%. If it helps, I'm using the Natty alpha as it is the only Ubuntu that has no display problems with my laptop.

---

### Post by abyrne on 2011-03-20
Yikes. If I guessed correctly, Sony Care probably deals with the battery (or some other power management devices) firmware. 9 out of 10 times, the protocol to change this firmware is proprietary. I'm not an expert, but you may need to reinstall windows to flip the firmware back to normal. Get a second opinion, though.

---

### Post by SekiTimewalker on 2011-03-20
Is there a good windows emulator I could use? I won't be able to get a legit Windows CD until September when I go back to college, as I get them free from the college.

---

### Post by abyrne on 2011-03-20
I don't think an emulator will work. Sony Care will probably need direct access to your computer's hardware, something an emulator is not capable of.

---

### Post by SekiTimewalker on 2011-03-20
Ok, thanks. I'll just deal with it until September. It's not a big thing as my computer is usually plugged in, just a small annoyance at having halfed my battery life until then.

---

### Post by abyrne on 2011-03-20
If you have another Windows box around, you could try building a WinPE (Windows Pre-Installation Environment). PEs are like live watered-down Live-CDs for Windows, and often they can run regular Windows applications. I don't know if Sony Care will work with it, but I guess it's worth a shot.

If you want to try it (and that Windows box you have is running XP), I recommend [BartPE]("http://www.nu2.nu/pebuilder/").

---

