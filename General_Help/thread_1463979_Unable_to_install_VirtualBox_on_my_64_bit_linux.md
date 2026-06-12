---
title: "Unable to install VirtualBox on my 64 bit linux"
date: 2010-04-27
forum: General Help
---

### Post by sgsawant on 2010-04-27
```
Error: Dependency is not satisfiable: libqt4-network (>= 4.5.1)
```

This is what I get when I try to install VirtualBox. Does it mean that I should downgrade my libqt4? If yes please tell how.

Regards,

-sgsawant

---

### Post by akand074 on 2010-04-27
Try this:

```
sudo apt-get install libqt4-network 
```

Should install the dependency your missing and then try reinstalling. Odd though it never did that when I installed it, I thought it installed dependencies automatically. Well give it a try. Sometimes when you get errors (atleast through the command line) it tells you what to try to fix it.

---

### Post by bodhi.zazen on 2010-04-27
try

```
sudo apt-get update
sudo apt-get install virtualbox
sudo apt-get install -f
```

---

### Post by P4man on 2010-04-27
I think it means libqt4-network is already installed, but an older version. Maybe you installed something outside of the repository?

---

### Post by dcstar on 2010-04-28
Or maybe this VM question has already been answered in the Virtualization forum (where all VM posts should be), has anybody looked?

---

