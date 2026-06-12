---
title: "upgraded to 9.10 from 9.04, still looking for 9.04?"
date: 2010-11-28
forum: General Help
---

### Post by alvinmoneypit on 2010-11-28
Hi,

Upgraded this laptop today (Lenovo N500) to 9.10, looking to go to 10.04 after I get it settled in, but why is synaptic package manager still looking for 9.04 packages and it looks for the cd stating "some packages were not found,  jaunty jackalope 9.04 cd-rom"  or something very similar.

Thanks for all responses.

---

### Post by new_tolinux on 2010-11-28
Is the 9.04-CD still listed in your list with sources (first tab in packet sources, but I'm not running the English version) and enabled?
If so, disable it ;)

---

### Post by alvinmoneypit on 2010-11-28
In this screen, it is not one I can disable.  It is a big block with bold print reading, "To install from CD-ROM insert CD" .

No, 9.04 CD is not on this screen, nor is it 'enabled'

---

### Post by garvinrick4 on 2010-11-28
Go to software sources; Is the cd box checked: uncheck it.

---

### Post by garvinrick4 on 2010-11-28
On the top of this page put a comment sign (#) in front of cdrom line. And then save.
#deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by alvinmoneypit on 2010-11-29
I don't have a box to check.

I did the edit of the source list via terminal as you suggest.

---

### Post by alvinmoneypit on 2010-11-29
rick,

I made the changes you suggested to the sources list through the terminal.  It looks like update manager is working properly now with no errors.

Thanks!

---

