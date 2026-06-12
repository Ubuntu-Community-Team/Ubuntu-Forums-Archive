---
title: "disable update-notifier?"
date: 2006-02-28
forum: General Help
---

### Post by acorrigan on 2006-02-28
I was just using mythtv and all of a sudden it started skipping like crazy during playback of recordings and while watching livetv.  I exited mythtv, went to system monitor saw that update-notifier was the only thing using the cpu, killed it, then went back to mythtv and the skipping was gone.

In the future since I don't want update-notifier to interfere with recordings and having to manually kill it is annoying.   How do I disable it permanently?

I tried uninstalling it, but it is a dependency of ubuntu-desktop, which I'm guessing is something I absolutely should not remove.  
I checked services, but didn't see it there.
I checked synaptic's options but didn't see anything there.

---

### Post by kaamos on 2006-02-28
You can just uninstall it. Ubuntu-desktop is just a metapackage used to pull in other packages like evolution and openoffice.

---

### Post by jrib on 2006-02-28
kaamos is right, but if you right click on it there should be some preferences you can use to stop it from checking for updates

---

### Post by MartinG on 2006-02-28
You should be safe uninstalling it.  Ubuntu-desktop is just a meta-package listing all the components of a standard desktop install, and doesn't do anything on its own. So, if you uninstall ubuntu-desktop with the notifier you should be fine -- but do check to see what else it will uninstall!

You should probably re-install ubuntu-desktop before doing a dist-upgrade, to ensure everything goes smoothly, but you could remove it again afterwards.

---

### Post by acorrigan on 2006-02-28
thanks for the advice and info everyone, I have now removed both ubuntu-desktop and update-notifier

---

### Post by engla on 2006-02-28
You could also remove it from your session..

Open session properties, remove it there and 'apply'. Then you have to save your changes when you log out (everything else you changed/added will be saved too)

---

