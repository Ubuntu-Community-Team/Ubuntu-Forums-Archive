---
title: "Jaunty - Openoffice.org does not start anymore"
date: 2009-10-04
forum: General Help
---

### Post by DeadMetal on 2009-10-04
Hi,

In Jaunty, without having done anything 'dangerous', my Openoffice.org stopped working a couple of days ago.

When I run it from the terminal:

daniel@Daniel:~$ ooffice -calc
/usr/lib/openoffice/program/soffice.bin: symbol lookup error: /usr/lib/openoffice/program/../basis-link/program/libsfxli.so: undefined symbol: _ZN6SvLBox16NotifyAcceptDropEP11SvLBoxEntry

daniel@Daniel:~$ ooffice -writer
/usr/lib/openoffice/program/soffice.bin: symbol lookup error: /usr/lib/openoffice/program/../basis-link/program/libsfxli.so: undefined symbol: _ZN6SvLBox16NotifyAcceptDropEP11SvLBoxEntry

Does anyone have any idea how I can fix this? Thanks!

---

### Post by Hagar Delest on 2009-10-05
Try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by DeadMetal on 2009-10-06
I have found the solution. In Synaptic I selected all openoffice.org packages and marked them for reinstalling. After reinstallation, OpenOffice.org worked fine again.

Thanks for the suggestion though.

---

