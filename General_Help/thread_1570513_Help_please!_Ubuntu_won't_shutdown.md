---
title: "Help please! Ubuntu won't shutdown"
date: 2010-09-08
forum: General Help
---

### Post by Naoko15 on 2010-09-08
Hello, i've been trying to solve this issue for a few days now. 

I made a  fresh install of Ubuntu 10.04 in a Packard Bell Easynote V5908 laptop. The graphic chip is Intel. 

My problem is that there's no way i can make it shutdown. Restart works ok. It freezes  during the logo screen with the dots and i have to shut it down with the power on/off button.

These are the things i tried with no luck: 

* sudo shutdown -P now

* sudo halt

* sudo poweroff

* sudo shutdown -h now

* sudo init 0

* added "apm power_off=1" to modules

* Checked that there's no Open Office process running in the background while shutdown

* Reinstalled initscripts

* added "acpi=force" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
resulting in freezing during shutdown with black screen that says:

```

Deactivating swap

Will now halt

[50.770036] Power down


```
I read here that it might be a Lucid Lynx bug, so i upgraded to Ubuntu 10.10 beta and downgraded to 9.10...both resulting in the same behaviour. 

Help please, i'm desperate...don't know what else to try. All ideas will be very apprecciated.

Thank you!

---

### Post by Achilles124 on 2010-09-08
Boot in safe-mode?

or check the os for errors with a live-cd. (I know there is an option on the Live-cd for that).

---

### Post by Naoko15 on 2010-09-08
Thank you for your reply, 

I tried shutting the computer down in safe graphic mode and it freezes before getting to the logo screen, leaving the wallpaper and the cursor only. It won't let me move the mouse or do anything. 

Where's the option to check the os' errors in the live cd?

---

### Post by Naoko15 on 2010-09-09
I've updated the bios, just in case it fixed the problem with no luck. It shutdown properly the first time after updating, but it hasn't since then 

I've run out of ideas. Is it that my laptop isn't compatible with Ubuntu? 

Anything else that i might try?

:(

---

### Post by endotherm on 2010-09-09
based on the output, it looks like all the software is shut down and the disks unmounted, so all that remains is the physical power down. it sucks, but at least you won't damage your disks by hitting the power button to finish bringing it down. It may be slightly incompatible, but it sounds workable. with the upgrades, downgrades and betas however, I would recomend doing a clean install. the option to check the contents of your CD is on the main menu for the live CD.

if for some reason it fails to shutdown, and your disks are still mounted, you can hold Alt + PrntScrn and slowly type r e i s u b 
to safely bring it down.

---

### Post by Naoko15 on 2010-09-09
A clean install doesn't work either. I guess i'll have to make do with this issue. 

Thank you for your reply

---

### Post by ottosykora on 2010-09-09
After update to 10.04, my old dell C600 does also not shut down completely. I have to use the power switch for that. It is not so big problem, since it looks like the apps are all down, the os somehow too, just the computer does not physicaly switch off.
All did work on 9.10.

But if this was the only problem, many of us lived with that for years on w98se....

---

### Post by stevebu56 on 2010-09-09
Here's a thread that is talking about a similar issue. 

[http://ubuntuforums.org/showthread.php?t=1342787](http://ubuntuforums.org/showthread.php?t=1342787)

---

