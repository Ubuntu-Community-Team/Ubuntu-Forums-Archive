---
title: "Gedit opens an extra new tab when called from 'Run' box"
date: 2012-05-11
forum: General Help
---

### Post by EzioAuditore on 2012-05-11
Hi,

Using ubuntu Precise with unity shell. 

Problem:

Hit Alt+F2 and say, enter this "gksudo gedit /etc/default/grub"; gedit opens the file but an extra new tab titled "Untitle Document" also opens and when i close i get the annoying dialog stating if i want to save that untitled document which ofcourse i don't as its just empty.

But when called from terminal using "sudo gedit /etc/default/grub"; gedit opens with only the file and not any extra tab.

But i use the Run command a lot and its very annoying.. 

Any solutions or have i encountered a bug?

---

### Post by brainwash on 2012-05-11
Yeah, this bug still exists in Ubuntu 12.04. Link to the bug report:

[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/796076](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/796076)

---

### Post by EzioAuditore on 2012-05-11
> **brainwash said:**
> Yeah, this bug still exists in Ubuntu 12.04. Link to the bug report:

[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/796076](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/796076)

Sad it hasn't been fixed yet...:(

---

### Post by ajgreeny on 2012-05-11
It's the same if you open it from terminal with ```
gksudo gedit <filename>
``` to edit a root owned file.  Not a disaster, but annoying when you close the gedit window and you are asked if you wish to save "untitled".

---

### Post by EzioAuditore on 2012-05-11
> **ajgreeny said:**
> It's the same if you open it from terminal with ```
gksudo gedit <filename>
``` to edit a root owned file.  Not a disaster, but annoying when you close the gedit window and you are asked if you wish to save "untitled".

Yeah but it doesn't happen with sudo. I guess, the problem lies with gksu/gksudo itself.

---

