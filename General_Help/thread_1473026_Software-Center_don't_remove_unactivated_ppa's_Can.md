---
title: "Software-Center don't remove unactivated ppa's Cancel"
date: 2010-05-04
forum: General Help
---

### Post by markinf on 2010-05-04
I posted this bug on launchpad and still no anwser...
I thought that maybe posting here would find more users with the same bug.

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/574155]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/574155")

Binary package hint: software-center

Clean Lucid install =]

When you remove a ppa from Lucid it won't go away from Software-Center.

Steps to reproduce.
1) Install a third party ppa.
2) Update apt db.
3) Start Software Center, ppa will be enabled.
4) Remove third party ppa.
5) Start Software Center, ppa is still enabled.

---

### Post by zvacet on 2010-05-05
This is just suggestion,bit after step 4 try to update data base again and see if that works.

---

