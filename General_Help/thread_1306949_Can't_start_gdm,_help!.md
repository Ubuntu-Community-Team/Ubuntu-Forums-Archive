---
title: "Can't start gdm, help!"
date: 2009-10-30
forum: General Help
---

### Post by Jerfo on 2009-10-30
Ok, I think I really screwed it this time, I just installed Karmic today and was trying to reinstall my videocard, a damn Radeon 9200 which is like a ride through hell to get installed (if you can help on this while you're at it, that'd certainly be great!) and after restarting my computer it suddenly comes up with the command line version, not knowing what to do I started with the live cd and searched for some info about how to start it from command line and I tried the following:

startx
sudo /etc/init.d/gdm restart
sudo dpkg-reconfigure xserver-xorg
sudo apt-get update
sudo apt-get install ubuntu-desktop

neither of them worked, they gave various error messages which were lengthy and incomprehensible for me (except for ubuntu-desktop which simply said it was the latest version).

Can anybody please tell me what the hell went wrong here and how can I get back on my beloved gdm?

---

