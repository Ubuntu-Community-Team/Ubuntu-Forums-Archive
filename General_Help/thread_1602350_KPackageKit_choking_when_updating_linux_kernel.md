---
title: "KPackageKit choking when updating linux kernel"
date: 2010-10-21
forum: General Help
---

### Post by G. Rodrigues on 2010-10-21
Pretty much what the title says. When trying to update, KPackageKit downloads the packages but when commiting the changes it chokes on the linux kernel package. After a long time (several minutes) it just exits with a cryptic "an unexpected error occured" (or some such). It then "locks" and I have to "unlock" it using the solution given me in another thread (titled KPackageKit locked).

Anyone has any idea what is going on, and better yet, a solution?

Note: running Kubuntu 10.04. Any extra information needed feel free to ask it.

TIA, regards,
G. Rodrigues

---

### Post by G. Rodrigues on 2010-10-22
> **G. Rodrigues said:**
> Pretty much what the title says.

<snip>

Solved the problem. Instead of using KPackageKit resorted to the command line and used

sudo apt-get autoclean

to clean the downloads cache and then

sudo apt-get autoremove

Upon this, apt-get suggested the upgrade of the linux kernel package. Agreed with it and the upgrade was made. Upon restarting and getting back online, KPackageKit fired up and I selected all updates. This time around everything went fine.

Marking it as solved. TIA, regards,
G. Rodrigues

---

