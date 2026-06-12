---
title: "share /home between Debian and Ubuntu"
date: 2011-07-13
forum: General Help
---

### Post by miklcct on 2011-07-13
I want to have exactly the same settings between Debian and Ubuntu. Is it a good idea to share /home between them? As I'm in an NFS environment, the user names and UIDs/GIDs are always the same.

---

### Post by Bucky Ball on 2011-07-13
When you install Ubuntu, choose manual partitioning and the partition you have set as /home in Debian, mark it to use but NOT to format. The existing /home partition will then be used by Ubuntu as well.

BUT ... you will have this, not just one folder in there:

/home/DebUser
/home/UbuUser

... if you follow me. It is the same /home partition with two different user directories in it. I have three installs on my machine and thus my /home partition has three user folders in it (all of which I can access from any install so works great for me). 

Hope that helps.

---

### Post by CatKiller on 2011-07-13
> **miklcct said:**
> I want to have exactly the same settings between Debian and Ubuntu. Is it a good idea to share /home between them?

Not necessarily. Configuration file syntax sometimes changes with different versions of programs. If you've got different versions of a package installed in Debian and Ubuntu it might cause you problems.

It'll work fine except for when it doesn't.

---

