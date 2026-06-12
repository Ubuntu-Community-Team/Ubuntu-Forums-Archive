---
title: "Using other harddisks without sudo"
date: 2006-03-04
forum: General Help
---

### Post by geniusvicks on 2006-03-04
Whenever I have to access any hard drive like hda3, etc. I have to sudo it. How can I access it without sudo-ing it?

---

### Post by engla on 2006-03-04
You mount it manually?

To let anyone mount it you have to make a /etc/fstab entry. For example, the entry for cdrom looks like this:
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

With these entries you can make hard drives automount (or not if you don't want to) and set other things, like make anyone mount them (like the cd, which specifies 'user' as an option).

Look up how to write an /etc/fstab entry for your hard disk, that would be safer than me telling you what to type in.

---

