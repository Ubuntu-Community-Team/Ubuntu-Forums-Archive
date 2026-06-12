---
title: "&quot;new &quot; status"
date: 2009-08-16
forum: General Help
---

### Post by ilna on 2009-08-16
It's funny, all docs I have found just say how to *deal* with the status, but nothing about what does it *mean*.

Do I understand well, it is just informative status, and it means "new packages since last *foregt-new*' action (and it is safe to forget at any time)?

---

### Post by ilna on 2009-08-17
Millions see, nobody knows... Unbelievable! :-)

---

### Post by credobyte on 2009-08-17
What are you talking about ( status .. for what ? ) ? :confused:

---

### Post by ilna on 2009-08-17
I mean last line here (see below). Also aptitude manual has places telling how to deal with "new" packages (in fact, we can use in search and "forget" them).

```
$ sudo aptitude -P -V -v safe-upgrade
[sudo] password for anli:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?]
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done

Current status: 0 broken [+0], 0 updates [+0], 194 new [+0].

```

---

