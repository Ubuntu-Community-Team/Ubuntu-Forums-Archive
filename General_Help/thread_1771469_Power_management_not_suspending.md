---
title: "Power management not suspending"
date: 2011-05-30
forum: General Help
---

### Post by chomlee on 2011-05-30
Ok, I am running a file server that can be accessed throughout the house.  I was able to successfully wake from suspend and it works beautifully.  Now what I need the computer to do is go to sleep after lets say 30 minutes of inactivity so that I never have to touch the computer and it will use minimal power until I need it.

Anyhow, I tried to set the settings in Power management and the only thing that happens is the display turns off.  the suspend on the desktop works fine, I can type in sudo pm-suspend and that works fine.  but the computer just wont go to suspend automatically by way of the power manager.

I have tried changing the /etc/pm/config.d/00sleep_module to say SLEEP_MODULE="uswsusp", but that only made the computer go into some crazy linux mode that I had to reboot from.  I had to change SLEEP_MODULE="kernel" (actually, I left it blank as it is the default).

I also turned off my screensaver so there wouldn't be any confusion from that.


I also ran cat /var/log/pm-powersave.log and I got a long list with the following being one of the main texts that kept repeating.
"/usr/lib/pm-utils/power.d/sched-powersave false:**sched policy powersave OFF"

Anyway, I have been looking for a solution for a couple of days now and I finally gave in and joined the Ubuntu community hopefully to see if anyone could help.

Thanks in advance!

---

### Post by chomlee on 2011-05-30
Anybody?  I thought this would be a simple "you need to set this value in this file to (on)" answer!

This is ridiculous that my system wont suspend by way of the power manager and I can't believe that nobody uses that function.

---

