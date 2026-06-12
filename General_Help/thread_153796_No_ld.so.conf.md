---
title: "No ld.so.conf"
date: 2006-04-01
forum: General Help
---

### Post by sprucio on 2006-04-01
Is it normal that I don't have the file /etc/ld.so.conf on my workstation?

---

### Post by dcstar on 2006-04-01
[QUOTE=sprucio]Is it normal that I don't have the file /etc/ld.so.conf on my workstation?[/QUOTE]
Could be, it is a 0 byte file on my system.

---

### Post by sprucio on 2006-04-01
I forget exactly what the use of this file is but doesn't this file contain the full path to other (non /lib or /usr/lib) shared files?

I suppose as long as applications don't depend on files located ...let's say in /usr/local/lib, it should be OK?

---

### Post by souki on 2006-04-01
[QUOTE=sprucio]I forget exactly what the use of this file is but doesn't this file contain the full path to other (non /lib or /usr/lib) shared files?[/QUOTE]
yes, it is used by ldconfig (see the man)

> I suppose as long as applications don't depend on files located ...let's say in /usr/local/lib, it should be OK?
yes, if you want to permanently add /usr/local/lib, just add the path in the ld.so.conf file

---

### Post by sprucio on 2006-04-03
Do I need to run "ldconfig" after I add lines to this file?

---

### Post by taurus on 2006-04-03
Yes, you do.

---

