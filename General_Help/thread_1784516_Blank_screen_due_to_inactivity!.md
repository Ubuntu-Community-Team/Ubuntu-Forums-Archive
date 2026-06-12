---
title: "Blank screen due to inactivity!"
date: 2011-06-17
forum: General Help
---

### Post by sureshms on 2011-06-17
hi all.. i'm running a real time software on ubuntu 11.04
i need it to run for at least 12 hours continuously..
but every time i run it, i hit this snag: "after about an hour, a blank screen appears but the audio can be heard in the background.."
sometimes this problem is solved by shaking the mouse, but not always.. i've uninstalled and disabled all screensavers.. i've also played around the power management option.. but the blank screen still comes.. what do u think is the problem?? solution please..

---

### Post by Wayne_V on 2011-06-17
check the dpms and/or screensaver settings  with xset (xset q).

---

### Post by sureshms on 2011-06-17
> **Wayne_V said:**
> check the dpms and/or screensaver settings  with xset (xset q).

Will it permanently disable the screensaver or will it last only till the next power off?? Im using ubuntu 11.04 and im unable to find the xorg.conf file.

---

### Post by Wayne_V on 2011-06-17
xset only changes settings for the current session.  they will be reset at next login.

---

### Post by sureshms on 2011-06-17
> **Wayne_V said:**
> xset only changes settings for the current session.  they will be reset at next login.

On using the Xset command ive found that the dpms option was enabled. Ive now disabled it using Xset -dpms. Just waiting to see if it solves the problem.. Thank you.

---

### Post by amauk on 2011-06-17
Are you using a standard LCD monitor, or something else

Some plasma displays have a built-in sleep mechanism to prevent screen burn-in (from paused game consoles, DVD players, etc.)
Control of this is obviously done on the display itself, and external to any device plugged into the display

---

### Post by sureshms on 2011-06-17
Yes. I am using a standard LCD monitor. Now ive disabled dpms and am waiting to see if the problem is solved. If it does solve the problem i just need a solution to make this permanent i.e unchanged by reboots..

---

### Post by sureshms on 2011-06-17
I left the system idle for 20 mins and the screen appeared again. This is after disabling dpms. The screen disappears when the mouse is moved. But this is not a viable option.Plz advice

---

### Post by sureshms on 2011-06-17
> **Wayne_V said:**
> check the dpms and/or screensaver settings  with xset (xset q).

Using the xset command i disabled dpms and switched off the screensaver. The problem has been solved temporarily. The screen dosent appear. But my main issue is to keep these settings even after reboots. How can this be done?

---

