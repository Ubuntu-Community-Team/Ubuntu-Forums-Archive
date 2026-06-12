---
title: "Unable to get global umask to work in Lubuntu"
date: 2010-11-12
forum: General Help
---

### Post by demccully on 2010-11-12
I've tried changing the umask to 007 in the locations listed below and as expected the terminal works correctly when creating new files, however the gui falls back to 022. Wondering if anyone has gotten this to work. I'm doing a full reboot between changes.
Thanks

Lubuntu 10.10

~/.bashrc
~/.profile
/etc/profile
/etc/login.defs

(and a few other places experimentally)

---

### Post by vodsdarov on 2011-08-26
Hello, I'm finding the same trouble on Lubuntu 11.04

Did you found any workaround to solve the umask issue?

---

### Post by vodsdarov on 2011-08-26
Actually it works in Lubuntu 11.04 whenever you temporary set umask through the terminal, and create files or folders using the terminal.

But when you shift to the file explorer it totally omits the umask settings.
As for me, it didn't produced any effect setting a new umask at the mentioned files.

---

