---
title: "Compiz/Unity Mess in 11.10"
date: 2011-10-15
forum: General Help
---

### Post by samstreet101 on 2011-10-15
Any help would be much appreciated.

I hope I'm not the only one with this problem. So far I'm having problems with what appears to be the integration of compiz and unity launcher. The screen edges refuse to work half the time for e.g. I have compiz scale function bound to bottom left screen edge and sometimes this just doesn't work for an entire session. The same goes for activating the launcher, sometimes when it dodges windows it just won't come back by nudging the left of the screen so I have to use the super key to get the launcher up again. Also when I change certain settings or what seems to be a certain ammount of settings in compiz (fiddling with the unity plugin, sometimes just enabling or disabling a feature like wobbly windows) the entire system hangs and is totally unresponsive.

Lastly (although I'm not as concerned about this one) gnome-shell has a weird graphics problem...the top bar and various bits of text in the shell appear scrambled and pixelated (I'd show a screenshot but the screen cap appears not to capture elements of only the shell)

My graphics adapter is an ATI Radeon HD 5570, using the FLGRX driver installed with jockey if that helps

---

### Post by samstreet101 on 2011-10-15
Hmmm partially solved,

Removed the FGLRX driver and installed the latest build of the open source ATI drivers and that seems to have gotten gnome 3 shell working now. However, screen edge issue with unity launcher persists. Any ideas?

---

### Post by MrNugget on 2011-10-16
Same problem here. I've got the Compiz-Scale plugin on (via CCSM), Window Picker For All Windows is set to the upper right corner. Sometimes it works, sometimes it doesn't. Any ideas?

---

### Post by marcio123 on 2011-10-16
I also had some problems with compiz. For example edges did not work.

But restarting compiz with "compiz --replace" helps and all features work.

Restarting Compiz makes launcher visible all the time (seems that there are two launchers) so to work with that You have to kill launcher

sudo killall unity-2d-launcher

hope it helps.

---

### Post by samstreet101 on 2011-10-18
> **marcio123 said:**
> I also had some problems with compiz. For example edges did not work.

But restarting compiz with "compiz --replace" helps and all features work.

Restarting Compiz makes launcher visible all the time (seems that there are two launchers) so to work with that You have to kill launcher

sudo killall unity-2d-launcher

hope it helps.

That helps Marcio thanks a lot, though it is a stop-gap solution, I hope it gets a proper fix soon, I haven't checked launchpad to see if its been filed yet

---

### Post by samstreet101 on 2011-10-21
Issue now seems to be completely solved by installing the updates that were just added a day or so ago to the update manager. Would be interested to know if these updates also solve everyone else's problem.

---

### Post by kilpikonna on 2011-10-23
The updates solved my problems, thanks!

---

