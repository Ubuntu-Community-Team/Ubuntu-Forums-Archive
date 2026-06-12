---
title: "List of recent files"
date: 2006-03-29
forum: General Help
---

### Post by ubuntuubuntu on 2006-03-29
Is there some way of cleaning the list of recent files from applications like OpenOffice and Acrobat Reader? Thanks!

---

### Post by aysiu on 2006-03-29
Yes.

It's stored in /home/username/.openoffice.org2/user/registry/data/org/openoffice/Office/.Common.xcu
That's a hidden file, so if you're using Nautilus, press Control-H in your home directory in order to see it.

To clear it out, close OpenOffice and then delete that file (either graphically or with the command *rm ~/.openoffice.org2/user/registry/data/org/openoffice/Office/.Common.xcu*). Then, restart OpenOffice.

---

### Post by ubuntuubuntu on 2006-03-30
What about Acrobat Reader? Thanks

---

### Post by aysiu on 2006-03-30
[QUOTE=ubuntuubuntu]What about Acrobat Reader? Thanks[/QUOTE] I'm just guessing (haven't tested this one), but maybe /home/username/.recently-used

---

### Post by ubuntuubuntu on 2006-04-09
It doesn't work for Adobe Reader. Does anyone know how to delete the list of recent files from Adobe Reader? Thank you.

---

