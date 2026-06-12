---
title: "Failed install"
date: 2006-06-02
forum: General Help
---

### Post by canadianwriterman on 2006-06-02
After looking forward to the final release of 6.06 to install on my brand new machine (see specs below), the install has failed. I've tried both the live CD and the alternate CD and neither of them will recognize my two CD ROMs. Kinda makes it impossible to get very far in the install. I went back to my old Breezy live CD and it went almost all the way, but could not start xorg server. Of course, I tried to gedit the conf file, but with no graphical interface, gedit won't work. ](*,)

---

### Post by bluevoodoo1 on 2006-06-02
[QUOTE=canadianwriterman]I tried to gedit the conf file, but with no graphical interface, gedit won't work. ](*,)[/QUOTE]

try using "nano"

---

### Post by cjazz on 2006-06-03
The other approach is to do

sudo dpkg-reconfigure xserver-xorg.

---

