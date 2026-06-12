---
title: "mysqld escapes schroot?"
date: 2010-11-19
forum: General Help
---

### Post by meonkeys on 2010-11-19
I made a chroot using debootstrap, then used apt in the chroot to install mysql-server-5.1. When I start the server with [FONT="Courier New"]sudo /sbin/initctl start mysql[/FONT] (again, inside the chroot), [FONT="Courier New"]/var/run/mysqld/mysqld.sock[/FONT] (the one **outside the chroot**) is overwritten!

Anyone know why/how that might be happening?

It also looks like mysqld in the chroot is using the datadir (/var/lib/mysql) outside the chroot.

---

### Post by meonkeys on 2010-11-19
Aha:

[LIST]
[*] [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430224](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430224)
[*] [https://wiki.ubuntu.com/KarmicKoala/ReleaseNotes#Upstart%20jobs%20cannot%20be%20run%20in%20a%20chroot](https://wiki.ubuntu.com/KarmicKoala/ReleaseNotes#Upstart%20jobs%20cannot%20be%20run%20in%20a%20chroot)
[/LIST]

---

