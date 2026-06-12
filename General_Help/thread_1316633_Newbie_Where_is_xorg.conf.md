---
title: "Newbie: Where is xorg.conf?"
date: 2009-11-06
forum: General Help
---

### Post by Listerofsmeg01 on 2009-11-06
I'm trying to increase my screen resolution in 9.10 and all the guides tell me to tweak /etc/X11/xorg.conf

The thing is I don't have an xorg.conf in that folder! Do I need to create one? Or have things changed since the guides were written.

(I'm running it in VirtualBox if that makes any difference)

Many thanks,
Lister

---

### Post by any.linux12 on 2009-11-06
> **Listerofsmeg01 said:**
> I'm trying to increase my screen resolution in 9.10 and all the guides tell me to tweak /etc/X11/xorg.conf

The thing is I don't have an xorg.conf in that folder! Do I need to create one? Or have things changed since the guides were written.

(I'm running it in VirtualBox if that makes any difference)

Many thanks,
Lister

Can't you just go to System->Preferences->Display ??

---

### Post by mortenr on 2009-11-06
Try using Places - Search for files to locate it. If it doesn't show up, open a terminal and run updatedb, then search again.

/etc/X11 is the default spot and I have mine there too. Dunno what VirtualBox should change about that...?

---

### Post by P4man on 2009-11-06
> **Listerofsmeg01 said:**
> I'm trying to increase my screen resolution in 9.10 and all the guides tell me to tweak /etc/X11/xorg.conf

The thing is I don't have an xorg.conf in that folder! Do I need to create one? Or have things changed since the guides were written.

(I'm running it in VirtualBox if that makes any difference)

Many thanks,
Lister

by default xorg.conf is empty.
But **running it in virtualbox** changes everything. You have to install the vbox guest additions
[http://www.virtualbox.org/manual/UserManual.html#guestadditions](http://www.virtualbox.org/manual/UserManual.html#guestadditions)

Then you will not have to touch xorg.conf. What host OS are you using?

---

### Post by Listerofsmeg01 on 2009-11-06
> **P4man said:**
> by default xorg.conf is empty.
But **running it in virtualbox** changes everything. You have to install the vbox guest additions
[http://www.virtualbox.org/manual/UserManual.html#guestadditions](http://www.virtualbox.org/manual/UserManual.html#guestadditions)

Then you will not have to touch xorg.conf. What host OS are you using?
Thanks, I just installed guest addtions so I could copy and paste onto here, and you're right, I now have an xorg.conf sat there.

Many thanks for everyone's help.

ETA: I'm using XP as host.

---

