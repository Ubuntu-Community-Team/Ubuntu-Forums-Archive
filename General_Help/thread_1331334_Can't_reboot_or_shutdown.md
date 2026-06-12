---
title: "Can't reboot or shutdown"
date: 2009-11-19
forum: General Help
---

### Post by GiganticDays on 2009-11-19
Recently installed Karmic Koala dual-booting with XP Pro on an AMD Quad Core system.
Installation went smoothly and I installed a few extras such as Thunderbird, Samsung's Unified Printer Driver (I have a CLX-2160 MFP) and the latest NVidia graphics driver.

Now the restart and shutdown menu commands do not work - no error message, just nothing.

This also happened yesterday after I installed the NVidia driver so I tried a hard reset of the PC but this resulted in Ubuntu booting to a terminal in the top let of an otherwise black screen. I could type commands and they would work eg. firefox started ok but startx didn't work.

Anyway, as a result of that I did a clean install of Ubuntu last night and reinstalled TB, Samsung driver and NVidia driver. Now, once again, the restart and shutdown commands don't work. I haven't forced a reboot using ctrl-alt-delete as I suspect I'll be left with the terminal screen again. Everything seems to run OK at the moment apart from the restart/shutdown issue.

I've tried uninstalling the NVidia and Samsung drivers but it hasn't solved the problem. Couldn't be Thunderbird could it?

---

### Post by GiganticDays on 2009-11-22
Well I think I might have answered my own question here. After a third reinstallation everything is working great.
What I think went wrong in the prior setups was that, because I prefer Thunderbird, I removed Evolution.
And since I'm a bit anal, I removed all Evolution packages without noticing that removing "evolution-data-server-common" also removed "gnome-applets", gnome-panel", and "ubuntu-desktop"

D-Oh!

Anyway all is now well and I'd just like to thank all those who contributed to this thread. Oh, hang on... it was just me ;)

---

### Post by cliffbreaker on 2009-11-22
You can reboot and shut down using command line. Open the terminal and do "sudo reboot" to reboot and  "sudo shutdown now" to shut your PC down.

---

