---
title: "Updated to 10.10...now no graphics?"
date: 2010-10-16
forum: General Help
---

### Post by kingmetalx on 2010-10-16
Hey guys,

I just updated my dual-booted (with XP) Ubuntu 10.04 to 10.10 via the Update Manager.  It looked as though everything went smoothly, but when I rebooted and selected the 10.10 in GRUB, it loads in a no-graphics mode and this is what I see:

* Checking battery state...     [OK]

Ubuntu 10.10 john-desktop-ubuntu tty1

john-desktop-ubuntu login: _

If I reboot and go into recovery mode and then load it in low-graphics mode, I see graphics again, but of course, in low-graphics.  Any ideas?

---

### Post by Quackers on 2010-10-16
What graphics card/driver are you running?

---

### Post by kingmetalx on 2010-10-16
GeForce4 MX 420.  nvidia_96.

---

### Post by Ubangi on 2010-10-19
I have the same problem

---

### Post by jim_deadlock on 2010-10-19
Try deleting /etc/X11/xorg.conf (or rename it) and then reboot. This fixed the problem for me.

---

### Post by tcpa41 on 2010-10-19
Sorry to bump this thread,but i also have nvidia-96 driver related problem. How should i install the driver if Ubuntu can't (for some odd reason) find in through Additional Drivers?

---

### Post by Rent_A_Pig on 2010-10-19
](*,)

---

### Post by kingmetalx on 2010-10-20
> **jim_deadlock said:**
> Try deleting /etc/X11/xorg.conf (or rename it) and then reboot. This fixed the problem for me.

When I right-click on xorg.conf, I cannot click Rename or Send To Trash...they are greyed out.  I am the administrator, as well.

---

### Post by jim_deadlock on 2010-10-21
You can do it in your terminal:

```
sudo rm /etc/X11/xorg.conf
```... or

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.save
```

---

### Post by kingmetalx on 2010-10-21
> **jim_deadlock said:**
> You can do it in your terminal:

```
sudo rm /etc/X11/xorg.conf
```... or

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.save
```

That did the trick.  Thank you very much!

---

