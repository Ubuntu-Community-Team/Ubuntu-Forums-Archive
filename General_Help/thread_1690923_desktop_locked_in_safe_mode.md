---
title: "desktop locked in safe mode"
date: 2011-02-19
forum: General Help
---

### Post by Bar2D2 on 2011-02-19
After using System-Administration-Login Screen Settings and choosing the Failsafe GNOME as default setting, it is not possible to change it back after a reboot and now a friend (don't ask why he played with this......) is stuck with his Ubuntu 10.10 Gnome session without any use of applications.
When he goes the the Login Screen Settings he can't press the Unlock button, thats is, nothing happens.....

Any idea how to solve this please?

---

### Post by ZootNerper on 2011-02-19
OK, I have solved it for me. This is what I did.

1) Open a terminal
2) type: gksudo gedit /etc/gdm/custom.conf
3) The last line should look something
     like this:     DefaultSession=gnome-failsafe   (not sure of exact wording of failsafe bit)
     Change it to:  DefaultSession=gnome
4) Save file and reboot

That's it.

Hope it works

-- Zoot

---

### Post by Bar2D2 on 2011-02-20
Excellent, the conf file is what I was looking for :-)
Thanks a million!

___SOLVED___

---

### Post by christo91 on 2011-04-13
Thanx a lot :-)

---

