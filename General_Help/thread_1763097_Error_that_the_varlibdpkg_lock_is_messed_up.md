---
title: "Error that the var/lib/dpkg lock is messed up"
date: 2011-05-20
forum: General Help
---

### Post by Drewby511 on 2011-05-20
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
This is the error I keep getting in the Terminal any help to fix it?

---

### Post by linuxinstalledfromhdd on 2011-05-20
I would reboot and run the recovery mode.  You will see it below the first grub entry. Arrow down and select it. Run fix broken packages, and see if that fixes it.

---

### Post by Rubi1200 on 2011-05-20
> **Drewby511 said:**
> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
This is the error I keep getting in the Terminal any help to fix it?
Hi and welcome to the forums :-)

That message usually indicates that you have more than one package manager open. For example, you cannot use the terminal and have, say, Synaptic open. Same applies to Ubuntu Software Center and Synaptic or any other combination.

Close all instances of package managers and then try again.

---

