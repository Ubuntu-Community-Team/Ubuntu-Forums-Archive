---
title: "viewing zipped files automatically (command line)"
date: 2006-05-24
forum: General Help
---

### Post by Erwin123 on 2006-05-24
Hi there,

with SuSE it is possible to view zipped files directly from the command line, ie. without explicitely unzipping them.

Examples:
gv manual.ps.gz
less README.gz

How do I configure Ubuntu to so as well?
Thanks!

Erwin

---

### Post by ifokkema on 2006-05-24
Hi,

You can use 'less':
less file.gz

For it to work, you must have this line in your ~/.bashrc:
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

HTH,

Ivo

---

### Post by Erwin123 on 2006-06-03
Works. Thank you!
Erwin

---

