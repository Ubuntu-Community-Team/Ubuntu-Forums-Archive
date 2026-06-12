---
title: "Removal of gnome packages causes boot stalls"
date: 2011-10-16
forum: General Help
---

### Post by mindsystem on 2011-10-16
Upgraded to 10.10 and "solved" the issues with that, but then decided I don't like the gnome3 interface, so I installed xubuntu-desktop and removed ubuntu-desktop with its extra stuff I didn't need. Everything was hunky-dory.
But then I tried decided that there was a bunch of gnome packages that were just chilling out doing nothing and taking up space, so I removed them (didn't remove any that were dependents of gdm [as I've read xfce needs it]) and on a reboot to get things working again.
Now on a normal boot, it stalls with "Checking battery state" (as before), which I realize I need to reinstall the nvidia-173 package to fix. But when I go into recovery mode and try "Resume normal boot" which worked in the past, it stalls at "gdm start". And when I log into the root shell (with or without networking), I can't connect to the internet because when I run "dclient eth0", it tells me I can't do that because it's a services job.

So:
1) I basically need to know how to dhclient to work
2) Which packages would I need installed to make my desktop work again?

If I can't get the internet working on the desktop, I can still wget the packages from my laptop and transfer them with a usb.

Bonus points: Is there another program ala lightdm and gdm that I could use instead of those two options? Preferably more lightweight.

---

### Post by mindsystem on 2011-10-16
Update: I was able to boot into a non-graphics terminal mode by using the 2.6 kernel in recovery mode, and was able to reinstall xubuntu-desktop, nvidia-common, and nvidia-173. But it still stalls when using normal 2.6 mode and either of the kernel 3 modes. Any ideas?

---

