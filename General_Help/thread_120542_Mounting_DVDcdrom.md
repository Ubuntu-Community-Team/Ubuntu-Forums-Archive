---
title: "Mounting DVD/cdrom"
date: 2006-01-22
forum: General Help
---

### Post by josel on 2006-01-22
I cannot access cdrom-drive unless accessed as root user.
Everything is correct- as far as i can see- under System and Preferences.  The behaviour is the on either gnome or KDE  and i've checked that the user is part og cdrom group. Everything worked fine before - i think the problem came when upgrading to breezy but i'm not sure.

Any help appreciated.

---

### Post by dcstar on 2006-01-23
[QUOTE=josel]I cannot access cdrom-drive unless accessed as root user.
Everything is correct- as far as i can see- under System and Preferences.  The behaviour is the on either gnome or KDE  and i've checked that the user is part og cdrom group. Everything worked fine before - i think the problem came when upgrading to breezy but i'm not sure.

Any help appreciated.[/QUOTE]
Tell us **exactly** what happens when you try.

---

### Post by ahh_dee on 2006-01-23
I can mount my drive fine with my /etc/fstab setting as


/dev/hdc /mnt/dvdrom udf,iso9660 user,noauto 0 0

---

