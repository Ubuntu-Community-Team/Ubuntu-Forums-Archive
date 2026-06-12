---
title: "Karmic to Lucid = Less battery"
date: 2010-06-23
forum: General Help
---

### Post by linduxed on 2010-06-23
I upgraded from Karmic to Lucid some time ago and while I've generally been satisfied with the experience, my battery life went down from 7-9 hours all the way down to 3-5 hours.

This is quite an issue considering we're talking about an eeePC, which is supposed to be an unplugged device.

My suite of manually installed packages hasn't changed in any substantial way and my usage habits haven't either.
I've tried using powertop to squeeze out some more life out of the battery (which I pretty much never did before) but no big increases have been noticed.

If you need any data to solve this mystery, I'll provide it as soon as possible.

---

### Post by kabloink on 2010-06-23
It might be the cpu scaling bug. Some people including myself have problems with the cpu being stuck on performance instead of ondemand. I usually have to manually change the scaling mode using the gnome cpu scaling frequency monitor.

The other problem I ran into was ubuntuone wasting cpu cycles and eating up memory even though I never used it. Uninstalling it solved that problem.

---

### Post by warfacegod on 2010-06-23
1st Please update your profile, it still says 9.04 and that can be confusing. Thanks.:p

2nd I doubt there's any big mystery here. Doing an Upgrade Install is probably the culprit here. Backup your stuff and do a fresh install.

Other things that might help if a fresh install isn't an option.

Turn off Compiz, in other words under Appearances> Visual Effects> set to None

System> Prefs.> Startup Apps> disable as much as you can without rendering your system useless.

Reduce the backlighting while on battery, spindown HDD's when possible. Both are found in Power Management.

Set your screensaver to Blankscreen.

---

### Post by linduxed on 2010-06-23
I'm logging in to a clean awesome session (the WM "awesome") that has no autostart applications.

I start a terminal and enter this command:

```
gnome-settings-daemon & gnome-screensaver & nm-applet & gnome-power-manager & gnome-do & eeepc-tray.exe & update-notifier & gnome-keyring-daemon & thunderbird & firefox & exit
```

That's basically all that is running on my machine. I've set all the Power Management things.

Still, I needed nothing like this in Karmic.

---

### Post by warfacegod on 2010-06-23
Try watching your System Monitor to see if anything looks like it is using allot of processor time.


Although, I still think this is an Upgrade issue.

---

