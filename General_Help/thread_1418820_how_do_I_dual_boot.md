---
title: "how do I dual boot?"
date: 2010-03-01
forum: General Help
---

### Post by klasjosh30 on 2010-03-01
I want to dual boot with windows 7. How would I go about making a partition ect. for windows?

I know how to dual boot other OS's off of windows but not linux.

I just want to dual boot with ubuntu and windows 7

---

### Post by crlang13 on 2010-03-01
It shouldn't be a problem.  I haven't heard of any problems dual booting with Windows 7.

Windows needs to be installed first (otherwise windows formats before it installs).  Then, all you have to do is boot from the live cd ([http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)).

There is configuration software within the live CD that allows you to set up the partitions

---

### Post by Arkitekt on 2010-03-01
I currently am dual booted with UNR and Windows 7, and no.. windows does not need to be installed first as long as a partition is already made for it to install into (you would need to reinstall grub through a livecd/liveusb afterwards though so it is easier to install windows then ubuntu).

Easiest way to edit partitions in Ubuntu is with Gparted (sudo apt-get install gparted), not sure if gparted is included with the livecd/liveusb though.

---

### Post by OrangeCrate on 2010-03-01
An excellent set of dual booting instructions is here:

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

---

