---
title: "Lucid: Nvidia 96 log out causes hard lock up"
date: 2010-05-02
forum: General Help
---

### Post by rmrees on 2010-05-02
I've searched here, Kubuntu, & Google to no avail.
After installing Nvidia 96 (got an ancient MX4000) drivers via jockey & package managers (even Synaptic in Kubuntu), a log out causes a hard lock up - no keyboard response at all (as evidenced by the NUM lock LED not toggling).  I've tried the various Plymouth work arounds and now think it's an issue with KDM since I see a scrambled log in dialog for a brief moment and then black screen.
 
I did see a thread regarding GDM lock ups and nvidia 96 drivers, but nothing on KDM.
 
I can Restart and Shut Down from my account, but not log out, further evidence that KDM <> nvidia may be the evil combination.
 
I'm open to any information I can provide to help those with this issue.  Please let me know.
 
Thanks!

---

### Post by rmrees on 2010-05-03
Additional info:
Same HW - MX4000 GPU
Loaded Ubuntu 10.04 LTS - no problem with log out lock up.  Appears to be only related to nvidia 96 driver & KDM.

I've switched to Gnome anyway; like the looks, functionality, & performance.  KDE very slow in comparison.

Got compiz working on Ubuntu 10.04, too.  Don't forget to modify xorg.conf this way:

Code:
sudo nvidia-xconfig --add-argb-glx-visuals -d 24

Ubuntu 10.04 good so far, but took over 1 hour to load!
Can't say the same for Kubuntu 10.04 although.

---

