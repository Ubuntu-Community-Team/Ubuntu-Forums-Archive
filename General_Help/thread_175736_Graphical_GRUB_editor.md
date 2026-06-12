---
title: "Graphical GRUB editor?"
date: 2006-05-13
forum: General Help
---

### Post by _linux_ on 2006-05-13
Does anyone know of a graphical GRUB editor for Ubuntu? I don't really like opening the GRUB configuration file every time I need to change someting.

---

### Post by aysiu on 2006-05-13
See posts #13-15 of [this thread](http://www.ubuntuforums.org/showthread.php?t=149666).

---

### Post by az on 2006-05-13
[QUOTE=_linux_]Does anyone know of a graphical GRUB editor for Ubuntu? I don't really like opening the GRUB configuration file every time I need to change someting.[/QUOTE]
The gnome-system-tools used to provide one, but it got dissabled due to some severe bugs.  It would have been re-enabled for Dapper, but I don't know what happened.  You could always inquire upstream.   I think that the source for gnome-system-tools still provides boot-admin, but it is not built by default (dissabled in the debian/rules makefile).

[http://bugzilla.gnome.org/buglist.cgi?product=gnome-system-tools&bug_status=NEW&bug_status=REOPENED&bug_status=ASSIGNED&bug_status=UNCONFIRMED&component=boot-admin](http://bugzilla.gnome.org/buglist.cgi?product=gnome-system-tools&bug_status=NEW&bug_status=REOPENED&bug_status=ASSIGNED&bug_status=UNCONFIRMED&component=boot-admin)

---

### Post by Herman on 2006-05-13
> Does anyone know of a graphical GRUB editor for Ubuntu? I don't really like opening the GRUB configuration file every time I need to change someting. [GAG Boot Manager]("http://gag.sourceforge.net/") is a Graphical Boot Manager, but it is not specific to Ubuntu. GAG is 'operating system independant'.  It still requires either Grub or Lilo on either a seperate boot partition or the Ubuntu partition, which can be done during install or later on. It makes it easier if you change your disks and operating systems around quite often.
More info: [http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)
Regards, Herman

---

### Post by sargek on 2006-05-13
A graphical grub editor would open grub.conf to edit it as well, you just wouldn't "see" the config file, but the end result is the same. Maybe that's obvious, but grub.conf is pretty easy to edit.

---

### Post by beebelo on 2006-05-25
Glad to know why boot-admin is missing.  Actually I didn't know it existed; I've always just edited with nano.   I discovered its existance by accident when perusing Ubuntu Help in Dapper.  Help points users to boot-admin for editing GUIickly.  Help says it's found in System Tools, but it isn't there.  I also found it in the Debian menu, but it won't run....  Maybe boot-admin should be removed from Help.

---

