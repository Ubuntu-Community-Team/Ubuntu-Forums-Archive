---
title: "Startup Errors"
date: 2009-08-22
forum: General Help
---

### Post by radar56 on 2009-08-22
I recently installed Ubuntu and for a few times the startup worked fine (I am pretty sure).  Now I get a few errors when I startup my comptur (see attached).  Is this a concern?

Thank You

-adam

---

### Post by earthpigg on 2009-08-22
have you tried picking a different kernel version from your GRUB menu?

---

### Post by radar56 on 2009-08-22
The only other options are memtest and a recovery mode.  The recovery mode gives me a similar error.  as well as ata2: link is too slow to respond...

---

### Post by P4man on 2009-08-22
have a look at this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706)

There is a ton of workarounds in there, ranging from kernel parameters to changing hdd cables to leaving your cdrom drive open before booting (!). I suggest you read through it, and add your own report.

---

### Post by radar56 on 2009-08-22
It magically fixed it self, also now my cdrom drive mounts so is that linked or just coincidence?

---

### Post by P4man on 2009-08-22
I think its linked. many  people in that thread had problems with the cdrom drive, some cured it by updating its firmware (or disconnecting it).

The bad news is: if it solved itself like that, chances are it will come back by itself :s

---

