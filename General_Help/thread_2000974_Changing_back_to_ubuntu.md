---
title: "Changing back to ubuntu"
date: 2012-06-10
forum: General Help
---

### Post by Tombradyhasamachinehead on 2012-06-10
hi,
 I am using mint now but i want to switch back to ubuntu. My question is if i reformat my root parition with ubuntu that linux is on, will my /home parition files and settings be safe?

---

### Post by David Andersson on 2012-06-10
> **Tombradyhasamachinehead said:**
>  My question is if i reformat my root parition with ubuntu that linux is on, will my /home parition files and settings be safe?

It depends. If /home is on a separate partition it is safe, but you have to tell the new Ubuntu where it is during install, or fix it in /etc/fstab after install. (Of course, you must *not* tell Ubuntu to use the whole disk during the install.)

If you are unsure, I would recommend not to reformat. Just try install Ubuntu on top of Mint in the same partition. I have not tried this myself, but I think Ubuntu will detect the existing operating system and ask if to replace it, and that it will preserve /home.

In case I am totally wrong, make a backup of home first.

---

### Post by roelforg on 2012-06-10
> **david andersson said:**
> [s]in case i am totally wrong, [/s]make a backup of home first.

ftfy

---

