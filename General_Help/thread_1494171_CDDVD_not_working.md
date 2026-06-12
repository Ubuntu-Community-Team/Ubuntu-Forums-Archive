---
title: "CD/DVD not working"
date: 2010-05-26
forum: General Help
---

### Post by Autodave on 2010-05-26
I have 2 machines, both running Ubuntu 10.4 and I have the same problem on both of them: since the upgrade to 10.4, DVDs will not play in either machine.  When I try to open with Movie Player, it tells me that I may not have permission to use.  I did reboot the one machine with the DVD still in the tray and it worked then.  I tried the same thing with the other machine but it still gives the same error.

---

### Post by Autodave on 2010-05-26
> **Autodave said:**
> I have 2 machines, both running Ubuntu 10.4 and I have the same problem on both of them: since the upgrade to 10.4, DVDs will not play in either machine.  When I try to open with Movie Player, it tells me that I may not have permission to use.  I did reboot the one machine with the DVD still in the tray and it worked then.  I tried the same thing with the other machine but it still gives the same error.

More info: one of my DVD drives says that I am not the root owner and I cannot change the permissions.  Can someone tell me how I change the permissions?

---

### Post by GameDog(A) on 2010-05-26
I had the same problem, here is how I solved it.

Open Terminal and type

> sudo apt-get install libdvdread4 

and then

> sudo /usr/share/doc/libdvdread4/install-css.sh

Reboot and it should work.

---

### Post by Autodave on 2010-05-26
> **GameDog(A) said:**
> I had the same problem, here is how I solved it.

Open Terminal and type

 

and then



Reboot and it should work.

Still no good.  I have 2 DVD drives.  One drive's permissions are set for user -1, but the other is set for root.  How do I change the root one?

---

