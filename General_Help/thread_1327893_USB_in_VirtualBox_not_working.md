---
title: "USB in VirtualBox not working?"
date: 2009-11-15
forum: General Help
---

### Post by dserver on 2009-11-15
Hey fella's,

I'm having some difficulty in VM with adding USB devices. If I add a filter, all my USB devices show up but when I boot into the system all the check boxes are grayed out next to the device and I can't click them. I've tried a Windows host with Ubuntu guest, Windows host with Windows guest, Ubuntu host with Windows guest, and Ubuntu host with Ubuntu guest with no results. I'm currently working on a Windows host with an Ubuntu 9.04 guest. Any help would be much appreciated!

P.S. I have guest additions installed properly.

---

### Post by 3Miro on 2009-11-15
You have to add yourself as a member of the virtual box users group. Go to System -> Admin -> Users, unlock and go to groups. Add your user name to the group. (in KDE it is under system settings -> advanced -> user management)

In my case, in order to use my printer, I had to add myself as member of group ld as well.

---

### Post by dserver on 2009-11-15
I'm currently running Windows XP with an Ubuntu guest and there isn't a vbox group. If I get time tomorrow I'll install XP on my Ubuntu box to test this out though. The only reason it's not on there now is because it's a really old machine and VM doesn't run very smooth on it.

---

### Post by todak on 2009-11-15
USB support is not available in virtualbox-ose (open source edition). You need to purchase the closed-source edition from Sun. See [here]("http://www.virtualbox.org/wiki/Editions") for details.

Edit: Actually, you do not need to purchase it if you do not want support or are using it for personal use. You can download and install the closed source edition, however, you do not get the source code or any support from Sun unless you pay for a license.

---

### Post by dserver on 2009-11-16
Thank you so much! I wouldn't even have known. I'll try this tomorrow.

---

### Post by dserver on 2009-11-16
Yup, that was the problem. Thank you for your help!

---

