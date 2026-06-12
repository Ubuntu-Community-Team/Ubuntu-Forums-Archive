---
title: "problem after changing repository"
date: 2011-01-03
forum: General Help
---

### Post by wolfemanmarine on 2011-01-03
i reciently changed my repository to install adobe reader, i failed at installing it and managed to change my grub some how, now i can only boot into recovery mode. anyone know how to fix this?

---

### Post by ridgeland on 2011-01-04
From the command line try
$ grub
then hit tab 3 times
you'll get a list of the grub commands.
read more about one with
$ man grub-mkconfig
I've seen
update-grub
used.  Try
$ man update-grub
I think update-grub may be what you're asking about.

---

