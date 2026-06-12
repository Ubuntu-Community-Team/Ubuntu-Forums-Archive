---
title: "Good reliable 10.10 Machine failing to boot."
date: 2011-06-01
forum: General Help
---

### Post by Vigh on 2011-06-01
Hi,
 had a really good reliable machine going with 10.10, but for some reason upon powering up this morning is failing to boot. Any ideas on how to fix this problem greatly appreciated, i have already tried dropping to root shell un-installing reinstalling the gnome desktop but that doesn't appear to be the problem. Could it be some kind of hardware fault?

---

### Post by wannabegeek on 2011-06-01
Sounds like it boots, or else you couldn't get a shell...do you mean that Gnome doesn't load ?

Did you recent;y update the kernel ? I had a problem once, where I did a system update and 
the new kernel didn't like my funky video setup. I don't remember the details.

---

### Post by Vigh on 2011-06-01
Yeah its running the latest updates, I can get to shell, but thats it. Gnome doesn't start. Can also go into recovery mode and get to shell with networking. But yeah no luck with just removing and installing ubuntu-desktop and gdm.

---

### Post by wannabegeek on 2011-06-01
You can load an older kernel by entering the grub menu and just selecting a different kernel.
It won't hurt anything, since the change is only for that session.

I think xorg.conf still controls the monitor settings. Google that and see if you can confirm that 
this file did not change. If the monitor/graphics card settings are wrong,  Gnome won't run.

---

### Post by Vigh on 2011-06-01
Already tried, no luck with older kernel.

---

