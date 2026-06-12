---
title: "powersave and lock screen after resume settings being ignored"
date: 2010-05-02
forum: General Help
---

### Post by a-user on 2010-05-02
I disabled the suspend monitor setting in the powersavings menu. i disable lock screen on resume with gconf but neither works.

the settings are set and saved and persists even after reboot but they have no effect. after 10 or 15min my monitor goes black and after resume from suspend iallways get the password propt. it seems all settings have no effect.

---

### Post by a-user on 2010-05-03
no one some infos?

---

### Post by MoarningSun on 2010-05-05
For the issue of your monitor going black after some time: 
Have you checked the screensaver settings as well? They're in System > Preferences > Screensaver ;)

For the password after suspend: If you use Ubuntu 10.04 try [this]("http://ubuntuforums.org/showthread.php?t=1466504"). In 9.10, you could disable the lock screen after suspend by going this route: 

Hit Alt+F2 and type "gconf-editor" (launch as user, so no sudo or gksu !!)
Go to apps > gnome-power-manager > lock and uncheck everything
Hit ctrl+alt+delete and choose suspend

This should result in no locked screen at wakeup! Mind that there are many ways to initiate a suspend in Ubuntu and this doesn't work for all of them! (Because not all methods to suspend use these particular gconf-settings) If you don't need lock screen at all you should try to disable it all together: In the gconf-editor go to desktop > gnome > lockdown and check disable_lock_screen. Any of this helps?

---

### Post by a-user on 2010-05-06
i think i already explained that i already did this. read first post. it has been already all unchecked as i already wrote above.

all settings regarding this are getting ignored. also i get a black screen after some minutes although screensaver AND suspending monitor are disabled.

so it seem all powersave related options gtk are totally ignored.

but thanks for your interest.

---

### Post by MoarningSun on 2010-05-06
OK your first post says you have the settings set, but not which settings specifically. Its just that power management like this isn't very straightforward to setup in ubuntu.. unfortunately. I saw you've already found the relevant [bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/255228") :) Lets see how that turns out..

---

### Post by a-user on 2010-05-07
well i admit, i was not specific with what settings exactly i adjusted.

well, what finally worked was disabling lockscreen in gconf->desktop->lockdown.
the settings in gconf->app->powermaneger (or similar) didnt had any influence.

additionally, related to my blackscreen screensaver problem, changing it through "system->settings->screensaver settings" didn't stopped the screensaver "black screen". i had to change several options with gconf (dont remember what exactly i needed to change).

---

