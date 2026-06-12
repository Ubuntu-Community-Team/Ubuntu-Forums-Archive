---
title: "Juggling repositories"
date: 2012-08-17
forum: General Help
---

### Post by J V on 2012-08-17
So I installed xorg-edgers ppa to get the new nvidia driver and then it was put into x-swat ppa so I wanted to downgrade back to x-swat but now I've got a whole bunch of xorg-edgers stuff installed and if I just "Force version" it will remove half my system.

Is there an easy way to automatically downgrade all the xorg-edgers stuff without messing up all the packages dependant on them?

---

### Post by J V on 2012-08-17
Well... I tried to do it myself and now it's taken 15 minutes just to get 800x600 xserver up and running...

nvidia-settings is constantly telling me to nvidia-xconfig and restart X and that's not working at all...

I'd like my 1080p desktop back if anyone knows what's going on...

**Edit:** Woohoo, all the way up to 1024x768... now then...

ppa-purge wants me to uninstall over 200 packages including pretty much all of my system... None of the packages it wants to screw with are dependant on xorg-edgers... stupid pos...

---

### Post by J V on 2012-08-17
Dependancy hell... So many circular dependancies in xorg-edgers you can't downgrade a package without wiping your whole system because instead of just downgrading the dependancies it removes them, thus removing itself as a dependancy of the dependancy and everything dependant on it: Poof - where did my 300 packages go??...

---

