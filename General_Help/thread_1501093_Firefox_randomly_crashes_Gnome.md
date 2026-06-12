---
title: "Firefox randomly crashes Gnome"
date: 2010-06-03
forum: General Help
---

### Post by WA1DH on 2010-06-03
I've posted about this problem before, but I think I've finally narrowed it down to Firefox. It seems like when I have multiple tabs open in Firefox, at completely random, the screen goes black, and a bunch of terminal lines come across quickly, with the last one reading "Checking battery state." I am then taken to the Gnome login screen. When I log back in, of course, all of my work is gone (everything closed) and I'm back at a fresh desktop.

This problem only occurs on my laptop (IBM Thinkpad T40) with Lucid 10.04. It never occurred in 9.10. I have tried reinstalling Firefox via Synaptic with no effect. If I browse in Seamonkey, this does not happen. As much as I enjoy Firefox, I can't get any work done when everything keeps crashing. So, I'm hoping someone can point me in the right direction to fixing this problem so I can use Firefox once again.

Thanks.

---

### Post by gabak on 2010-06-03
plz report this bug
[https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

or go to terminal
sudo aptitude remove firefox

then reinstall it again

sudo aptitude install firefox

---

### Post by lovinglinux on 2010-06-03
Create a new Ubuntu user, login with the new account and test Firefox to see if the problem persists. Then report back. 

The new user will start with a clean slate, including new Firefox user profile and clean Gnome settings. This way you can determine if the problem is on your Firefox profile or Gnome settings at the same time.

Usually, Firefox problems are related to Firefox user profiles, but since you whole desktop is crashing, then I guess it could be some Gnome settings or video driver issues, triggered by Firefox.

---

