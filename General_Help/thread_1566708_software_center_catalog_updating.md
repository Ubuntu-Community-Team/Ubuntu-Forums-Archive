---
title: "software center catalog updating"
date: 2010-09-02
forum: General Help
---

### Post by dfd001 on 2010-09-02
Was looking at software center for MPlayer.  Under info, I got a line that said "To show information about this item, **software catalog needs updating**.

I realize this isn't a critical problam, but I am wondering if anybody can share with me just how to 'update the software catalog?"

Thank you

---

### Post by darolu on 2010-09-02
This "catalog updating" can't be done by users but by the people maintaining each package and/or the actual centre; it however updates its database (i.e. when new versions of the software come available) each time you look for upgrades (daily by default) like when you run: "sudo apt-get update" in your terminal.

---

### Post by Autodidact on 2010-09-02
It's a known bug (message should never show up):
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/604625](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/604625)

Make sure you have an working internet connection.
Open terminal and run "sudo apt-get update".
Now open Software Center again. The warning should be gone.

---

### Post by dfd001 on 2010-09-02
Thank you for your responses

---

