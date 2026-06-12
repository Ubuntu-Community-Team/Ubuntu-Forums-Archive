---
title: "Cannot reboot after switching to nvidia graphic card"
date: 2009-09-20
forum: General Help
---

### Post by voy on 2009-09-20
I switched to an nvidia graphics card, because it seems to be much better supported in linux than ati. The following problem appeared: (I suppose it must be related to this hardware change, because everything was alright before). When I try to restart my machine (be it from the shell or x) I end up with just a blank screen and have to restart manually (hardware reset). The whole operation seems to go ok up until some last point where the actuall reset should happen.

Any ideas? Logs to look at? Common causes of problems like this? Thanks in advance!

---

### Post by Woody1987 on 2009-09-20
go into recovery mode, select root terminal, type sudo apt-get install nvidia-glx-180, then sudo nvidia-xconfig. Reboot.

---

### Post by voy on 2009-09-21
Sorry for misunderstanding, my accelerated desktop works fine including compiz and everything, the only thing not working is system reboot. Otherwise my nvidia works well with the proprietary driver, it seems.

---

### Post by voy on 2009-10-03
Still can't reboot my computer after upgrade to nvidia w/ proprietary drivers. Anyone having the same issue?

---

### Post by akakingess on 2009-10-03
Just a shot in the dark, what happens if you boot with the LiveCD and then try to shutdown or restart?

---

### Post by voy on 2009-10-04
That was a good guess, akakingess - thank you. Live cd reboots just fine. So then it has to be due to some packages I've installed, perhaps some leftovers from when I was trying to get the ATI drivers to work. Or maybe it's my kernel (I use 2.6.30-10). Do you have an idea where I should look for debug information?

---

