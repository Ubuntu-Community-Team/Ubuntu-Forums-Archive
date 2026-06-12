---
title: "Ubuntu Karmic - Canoscan LIDE 50 - Failed to start scanner: Error during device I/O"
date: 2010-02-17
forum: General Help
---

### Post by G@Tenerife on 2010-02-17
Hello,

I just clean installed Ubuntu Karmic after having had my first, most pleasant experience with Ubuntu 9.04.

I use Canoscan LIDE 50 as my scanner, which is supported. On Ubuntu 9.04 it worked out of the box without any problem.
Since I installed Ubuntu 9.10, although it recognizes my scanner, I constantly receive the following error message when trying to scan - whatever software I use (Xsane, gscan2pdf, OpenOffice):
Xsane:
Failed to start scanner: Error during device I/O

gscan2pdf:
Error during device I/O

I also tried to run it by command in the Terminal:
scanimage >image.pnm
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
scanimage: sane_start: Error during device I/O

I have also checked my User privileges already, which are 100 % admin privileges.

[B]Anyone help me please to solve this issue?
Thanks in advance for the early reply.[/B]

---

### Post by zanetu on 2010-02-22
> **G@Tenerife said:**
> Hello,

I just clean installed Ubuntu Karmic after having had my first, most pleasant experience with Ubuntu 9.04.

I use Canoscan LIDE 50 as my scanner, which is supported. On Ubuntu 9.04 it worked out of the box without any problem.
Since I installed Ubuntu 9.10, although it recognizes my scanner, I constantly receive the following error message when trying to scan - whatever software I use (Xsane, gscan2pdf, OpenOffice):
Xsane:
Failed to start scanner: Error during device I/O

gscan2pdf:
Error during device I/O

I also tried to run it by command in the Terminal:
scanimage >image.pnm
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
scanimage: sane_start: Error during device I/O

I have also checked my User privileges already, which are 100 % admin privileges.

[B]Anyone help me please to solve this issue?
Thanks in advance for the early reply.[/B]

It seems to be a bug. You may try downgrading libsane to 1.0.19.
Reference: 
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/465055](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/465055)

---

### Post by G@Tenerife on 2010-03-06
Hello zanetu,

First, sorry for my late reply ... but a big THANK YOU!

I read this bug report and followed the advise given. Downgrading to libsane 1.0.19 works as long I do not restart my PC, but at least it's a good work-around.

As removing libsane 1.0.20 demands also to remove a few other files, I created a quick-reinstall list, which allows me to perform this downgrade procedure in a very fast way.

Thanks again for your advise.

---

