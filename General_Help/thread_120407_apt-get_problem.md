---
title: "apt-get problem"
date: 2006-01-21
forum: General Help
---

### Post by CosMix on 2006-01-21
Hello,

We have reinstalled Ubuntu (actually only GRUB) after some bootup trouble with Windows and Linux. Now whenever we try to use apt-get install we get several errors that look a bit like this:

"debconf: apt-extracttemplates failed: Bad file descriptorE: Cannot get debconf version. Is debconf installed?"

We tried to use "dpkg -l debconf" and we just get the following mysterios output: "dpkg: configuration error: unknown option log: Success".

What do we do to fix this?

Thanks for any help.

---

### Post by gabspeck on 2006-01-21
The right switch for installing a package using dpkg is -i, not a small L ;) (as in dpkg -i package.deb)

---

### Post by CosMix on 2006-01-21
[QUOTE=gabspeck]The right switch for installing a package using dpkg is -i, not a small L ;) (as in dpkg -i package.deb)[/QUOTE]

root@Linux:~# dpkg -i debconf
dpkg: configuration error: unknown option log: Success

---

