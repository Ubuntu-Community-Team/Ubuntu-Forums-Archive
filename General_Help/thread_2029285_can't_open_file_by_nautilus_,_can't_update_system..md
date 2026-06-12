---
title: "can't open file by nautilus , can't update system."
date: 2012-07-19
forum: General Help
---

### Post by sameer rahman on 2012-07-19
i am new in ubuntu.
after installing ubuntu i faced two major problem.

1> i can't open any file by nautilus. but if i run the command "sudo nautilus" it works.i want to browse my files generally.

2> when i want to update system,system show me this.........
       "Requires installation of untrusted packages
      The action would require the installation of packages from not authenticated sources."
   i also see this when i want to download apps by ubuntu software center.

please help me............:confused:

---

### Post by spjackson on 2012-07-19
> **sameer rahman said:**
> i am new in ubuntu.
after installing ubuntu i faced two major problem.

Welcome, and congratulations on your excellent choice!

> 
1> i can't open any file by nautilus. but if i run the command "sudo nautilus" it works.i want to browse my files generally.

Sometimes when a program is first run via sudo, it can create configuration files that are owned by root and not accessible by the normal user. This could possibly be what is happening here.

I suggest you run the following which makes you the owner of your home directory and everything below it.
```

sudo chown -R $USER:$USER ~

```

> 
2> when i want to update system,system show me this.........
       "Requires installation of untrusted packages
      The action would require the installation of packages from not authenticated sources."
   i also see this when i want to download apps by ubuntu software center.

please help me............:confused:

Which Ubuntu version is this? Do you know which packages it is complaining about? Can you post the contents of /etc/apt/sources.list ?

---

### Post by sameer rahman on 2012-07-20
thank you for your replay.source list given below.it is ubuntu 12.04. sorry to say that your command does not work.

/etc/apt/sources.list.d/diesch-testing-precise.list
/etc/apt/sources.list.d/diesch-testing-precise.list.save
/etc/apt/sources.list.d/indicator-multiload-stable-daily-precise.list
/etc/apt/sources.list.d/medibuntu.list
/etc/apt/sources.list.d/medibuntu.list.save
/etc/apt/sources.list.d/tualatrix-ppa-precise.list
/etc/apt/sources.list.d/tualatrix-ppa-precise.list.save
/etc/apt/sources.list.d/webupd8team-jupiter-precise.list
/etc/apt/sources.list.d/webupd8team-jupiter-precise.list.save

---

