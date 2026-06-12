---
title: "Problems after upgrade"
date: 2006-03-15
forum: General Help
---

### Post by Tibor60 on 2006-03-15
I installed the last upgrades and after it I have serious problems, Ubuntu is practically unusable:

1. xsane freezes all the times, and there is no way to go out other than turn out the computer, no ctrl-alt-backspace, no ctrl+alt+f1 can help to go out from freeze. Even in windows I have never the need of such a lot of restarting than now with ubuntu.

2. impossible to install, re-install any packages, I receive all the time at any program messages like this:

W: Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/pool/main/x/xaw3d/xaw3dg_1.5+E-8ubuntu1_i386.deb
  MD5Sum mismatch

or the same error message this MD5Sum mismatch on the repository site...
What to do to solve the problem?

---

### Post by mlind on 2006-03-15
what is your graphics card?

does *sudo shutdown -r now* freeze your computer too?

2) if your /etc/apt/sources contain any cdrom entries, comment or delete those then try *sudo apt-get clean all*

---

### Post by Tibor60 on 2006-03-16
Thanks, concerning the 2. questions all is OK, but xsane still freezes after a couple of scanning, completely, I must to turn out with the main PC switch and switch oin again to restart. I have a Viper 550 graphic card.

---

