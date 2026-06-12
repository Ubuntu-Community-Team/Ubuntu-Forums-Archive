---
title: "brother dcp-145c printers drivers on ubuntu 10.04 64bit"
date: 2011-09-18
forum: General Help
---

### Post by cris_1986 on 2011-09-18
hy, 
i have ubuntu 10.04 64bit.
i need help to install printer drivers brother dcp-145c.
i have found 32 bit version drivers but not 64 bit version.

Can you help me

---

### Post by cris_1986 on 2011-09-19
no one have the some problem?

---

### Post by davidvandoren on 2011-09-20
**ia32-libs** or **lib32stdc++** is required to be installed.

but that's for ubuntu 8 and 9.
see if it helps.

---

### Post by cris_1986 on 2011-09-20
how can i install this packages?

---

### Post by cris_1986 on 2011-09-20
ok, the printer work:

```
sudo dpkg -i --force-architecture dcp145ccupswrapper-1.1.2-2.i386.deb dcp145clpr-1.1.2-2.i386.deb
```


now i'm going to install the scanner

---

### Post by cris_1986 on 2011-09-20
To install the scanner:

```
sudo dpkg -i brscan-skey-0.2.1-3.amd64.deb brscan-0.2.4-0.amd64.deb
sudo gedit /lib/udev/rules.d/40-libsane.rules

```

Add this:
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

and then save the file.
Reboot.


PS: download all packages in brothers website

---

