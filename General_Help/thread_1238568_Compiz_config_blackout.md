---
title: "Compiz config blackout"
date: 2009-08-12
forum: General Help
---

### Post by AfterShockPivot on 2009-08-12
I had the problem when I enabled "blur" on CCSM, and now Ubuntu just starts getting black squares everywhere. I uninstalled "sudo apt-get remove compizconfig-settings-manager" with the fail proof console on log-in, but it still didn't change anything, HELP!!!

---

### Post by AfterShockPivot on 2009-08-12
No seriously I need help, I can't even use Ubuntu with this problem.

---

### Post by CatKiller on 2009-08-12
It's considered impolite to bump more than once a day. Not even waiting 20 minutes is extremely rude.

Removing compizconfig-settings-manager just means that you can't configure Compiz easily any more. Re-install it.

You might find it helpful to press Alt-F2 and type ```
metacity --replace
``` to temporarily switch window managers. That way, you'll be able to see what you're doing to disable the Blur plugin again. Then you can user ```
compiz --replace
``` to turn Compiz back on again.

---

### Post by AfterShockPivot on 2009-08-12
sorry about the bump, but posts always get buried so quickly here. Anyway, I can't even press Alt+F2 because it's black too. The only thing that works is console in failsafe mode on login.

---

### Post by CatKiller on 2009-08-12
> **AfterShockPivot said:**
> sorry about the bump, but posts always get buried so quickly here. Anyway, I can't even press Alt+F2 because it's black too. The only thing that works is console in failsafe mode on login.

The fact that it's black doesn't matter. The Run dialogue will still accept input, even though you can't see it. Just type carefully and you'll be fine.

EDIT: To clarify; there are other methods, but this is by far the simplest.

---

### Post by AfterShockPivot on 2009-08-12
Thanks, I'll try it.

---

### Post by CatKiller on 2009-08-12
[This]("http://ubuntuforums.org/showpost.php?p=7758641&postcount=6") is the complicated way, just so that you don't think I'm holding out on you.

---

### Post by AfterShockPivot on 2009-08-12
IT WORKED!!! Thanks

---

### Post by CatKiller on 2009-08-12
No worries :)

---

