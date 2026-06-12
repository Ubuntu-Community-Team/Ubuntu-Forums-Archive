---
title: "Duplicate sources.list entry"
date: 2011-08-20
forum: General Help
---

### Post by JohnE1 on 2011-08-20
Release: Latest Natty Narwhal (11.11 ?)

Synaptice Pkg Mgr gives the following error/warning message:

W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty/main i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty/restricted i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-i386_Packages)

FYI, I do want both the main and restricted package lists. This error resulted from following instructions to add the restricted repositories to my Sources.

TIA for help!

---

### Post by thefasterblueone on 2011-08-20
Please post the output of:

```
cat /etc/apt/sources.list
```

---

