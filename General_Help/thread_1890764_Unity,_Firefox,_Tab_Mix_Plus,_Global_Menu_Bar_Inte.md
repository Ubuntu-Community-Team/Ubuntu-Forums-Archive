---
title: "Unity, Firefox, Tab Mix Plus, Global Menu Bar Integration: conflicts"
date: 2011-12-04
forum: General Help
---

### Post by Paddy Landau on 2011-12-04
Firefox on Unity has an extra add-on called Global Menu Bar Integration. This integrates the Firefox menu with the Unity menu bar.

Unfortunately, it has a bizarre side-effect. It prevents session-restore in the [Tab Mix Plus add-on]("https://addons.mozilla.org/firefox/addon/tab-mix-plus/") from working properly (i.e. it disables Tools > Session Manager > Last Session).

I am using Natty 11.04. Does anyone have this problem on Oneiric 11.10 or Precise 12.04?

I cannot test 12.04 (the installer fails for me), but I will try loading 11.10 to see whether or not the same problem occurs.

---

### Post by Paddy Landau on 2011-12-04
I have tried on 11.10 and the same problem occurs.

I cannot test on 12.04 alpha because the Live USB hangs and the installer fails.

---

### Post by Paddy Landau on 2011-12-04
I have reported this as [a bug in Ubuntu]("https://bugs.launchpad.net/bugs/899975").

---

### Post by lovinglinux on 2011-12-04
Sometimes the Gobal Menu Bar integration extension also prevents Firefox from starting. I have seen many users reporting this problem in the past. I don't know if the problem has been resolved.

About the session issue, I recommend using [Session Manager](https://addons.mozilla.org/en-US/firefox/addon/session-manager/).

---

### Post by Paddy Landau on 2011-12-05
Thank you, I have installed Session Manager and it seems to work.

---

