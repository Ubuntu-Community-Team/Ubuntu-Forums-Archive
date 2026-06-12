---
title: "query for /etc/apt/sources.list"
date: 2006-03-29
forum: General Help
---

### Post by mohoso on 2006-03-29
I wanted to know how to uncomment a line in the /etc/apt/sources.list...
It sounds simple but am new to the Linux operating system.
Much regards if any one can help.
Mohoso

---

### Post by shuttleworthwannabe on 2006-03-29
how about jsut deleting the "#" before the line starts??You have to be root to do this
NOTE: make a backup of the file first
like so
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
then do
$sudo gedit /etc/apt/sources.list

edit the file and save.

---

### Post by aysiu on 2006-03-29
You can also go to System > Administration > Synaptic Package Manager and check the unchecked boxes in Settings > Repositories

---

