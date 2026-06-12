---
title: "Power Management and Screensaver"
date: 2009-07-13
forum: General Help
---

### Post by Andy06 on 2009-07-13
I saw that the power management minimum time that can be set to turn off display was 11 minutes with no way to adjust this. Then after almost a year of using linux, I realise that setting is in fact in Screensaver and is enabled and affects other things even if the screensaver is completely disabled.

Can this be regarded a bug or a design flaw? The settings for how long after no activity it should be regarded as idle should be power management, it should all at least be in one place anyway. Right now it gives the assumption that nothing in screensaver is active, yet some settings are.

BTW, with a 700MB .iso limit, they still bundle all those screensavers?? I mean are screensavers of any use except to kill the planet and raise power consumption? Aren't blanked or turned off screens much better?

---

### Post by Andy06 on 2009-07-15
Can anyone confirm this? If it seems like a design bug. I might file a bug on launchpad in time for it to be fixed for 9.04.

---

### Post by CatKiller on 2009-07-15
It used to be exposed through the Power Management GUI for whether or not gnome-power-manager should use the Screensaver settings for determining whether the computer was idle or not, but now it's only shown as a GConf key. It's /apps/gnome-power-manager/lock/use_screensaver_settings in gconf-editor, if you're interested.

They don't include **all** the screensavers. There are more in the repositories :)

---

### Post by Andy06 on 2009-07-16
Ok I checked, there are already like a gazillion bug reports about this. Some as old as 2006, still not fixed even when report status says "Confirmed". But now it has been included as part of the 100 bugs project to be fixed before Karmic, so lets see if it is done before 9.10.

---

### Post by Andy06 on 2009-07-19
There is another issue, apart from the slider duration depending on the Screensaver settings, the power management values are actually "wrong". If I set it to turn the display off after 3 minutes, it does not do so. Instead it turns off after 5 minutes (3 minutes + the 2 minutes it takes to consider it idle according to the screensaver settings).

A bug about this was marked as fixed, how so? Can anyone confirm or deny this?

Thanks

---

### Post by Andy06 on 2009-07-25
*bump*

---

### Post by Andy06 on 2009-07-29
Ok now it has been marked as invalid. There are some changes in Karmic. I'm not sure if this means that the bug won't be fixed and continue to manifest in Karmic, be fixed or become irrelevant due to the changes.

---

