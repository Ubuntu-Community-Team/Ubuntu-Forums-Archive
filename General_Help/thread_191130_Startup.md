---
title: "Startup"
date: 2006-06-07
forum: General Help
---

### Post by jitesh on 2006-06-07
Is there a way to make program auto-run on startup of a ubuntu server machine?

---

### Post by Flyn on 2006-06-07
By server do you mean no GUI?

---

### Post by xtacocorex on 2006-06-07
It might help to know what you are trying to do, if you want it on system startup or Gnome startup. 

For system startup it is possible with cron jobs that are set for reboot. I just replied to someone with this method here [http://ubuntuforums.org/showthread.php?p=1106586](http://ubuntuforums.org/showthread.php?p=1106586)

---

### Post by thasheep on 2006-06-07
You can add commands to /etc/rc.local and they will be executed at boot. Make sure to put them before the 'exit 0' line or else they won't get run.

---

