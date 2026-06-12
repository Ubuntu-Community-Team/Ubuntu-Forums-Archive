---
title: "very long booting time"
date: 2010-01-24
forum: General Help
---

### Post by aargov on 2010-01-24
[COLOR="Black"][/COLOR]i installed ubuntu 9.1 desktop edition on a P4 2.6 GHz cpu and on asus motherboard
it takes about 11 minutes from the boot action until it reaches the desktop
i'm stressing that the OS is the only one that i'm using on the computer
any help would be appreciated

SA

---

### Post by warfacegod on 2010-01-24
Do you have any externals powered on during boot?

I'd also check System> Preferences> Startup Applications and disable as much as seems reasonable.

---

### Post by oldfred on 2010-01-24
You can check your log files and look for lines that have very long times between them or are repeating after an error to try to narrow the problem down.

system/admistration log file viewer.  Some log files are empty like boot log but the booting information is in several others like kern.log, dmesg etc.

---

