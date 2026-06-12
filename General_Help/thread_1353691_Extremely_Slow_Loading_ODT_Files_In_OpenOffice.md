---
title: "Extremely Slow Loading ODT Files In OpenOffice"
date: 2009-12-13
forum: General Help
---

### Post by Mr Fredrick on 2009-12-13
Hi All,

I'm having problem loading odt files in OpenOffice Writer, its taking longer than a few minutes during which time the temp of my CPU goes to 75degC and it hogs 100% of one of the cores. Sometimes I am unable to get them to load at all.

Is anybody else having this problem and is there a solution?

Thanks is advance for any help,

MrFred.

PS. The files are about 80kb and don't contain any graphics or anything fancy, just text and tables.

---

### Post by Hagar Delest on 2009-12-13
Try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

Else, do you remember any change in the printer environment? change of printer/network address/...?

Or you can try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by jbphuket on 2010-12-22
> **Mr Fredrick said:**
> Hi All,

I'm having problem loading odt files in OpenOffice Writer, its taking longer than a few minutes during which time the temp of my CPU goes to 75degC and it hogs 100% of one of the cores. Sometimes I am unable to get them to load at all.

Is anybody else having this problem and is there a solution?

Thanks is advance for any help,

MrFred.

PS. The files are about 80kb and don't contain any graphics or anything fancy, just text and tables.
This  solution works for me. I changed  this in my /etc/hosts file
Code:
127.0.0.1    hostname localhost hostname.(none)
Replace*hostname*with your hostname. (If you don't know what your hostname is you can enter 'hostname' in a terminal)

Open Applications->Accessories->Terminal

and at the terminal enter
sudo gedit /etc/hosts
N.B. I added this fix for ubuntu 10.10:
change the address 127.0.0.1 in the line containing (none) to: 127.1.0.0
this prevents it from changing with every boot

---

