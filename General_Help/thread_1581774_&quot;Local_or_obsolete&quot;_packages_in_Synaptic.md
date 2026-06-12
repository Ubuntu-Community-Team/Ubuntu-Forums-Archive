---
title: "&quot;Local or obsolete&quot; packages in Synaptic"
date: 2010-09-25
forum: General Help
---

### Post by veggen on 2010-09-25
Today when I opened Synaptic it had a new section called "Installed (local or obsolete)" and it listed mplayer (among other things). The installed and latest versions where the same and attempting to remove it resulted in a prompt to remove a lot of another packages like GnomeMPlayer and Audacious!?? This doesn't make much sense, if the packages are obsolete, why are the latest versions the same? And why list them if they are still used by many applications?

---

### Post by veggen on 2010-09-25
I just need an explanation why are those packages "obsolete".... or just what Synaptic means by "local or obsolete"?

---

### Post by dcstar on 2010-09-26
> **veggen said:**
> Today when I opened Synaptic it had a new section called "Installed (local or obsolete)" and it listed mplayer (among other things). The installed and latest versions where the same and attempting to remove it resulted in a prompt to remove a lot of another packages like GnomeMPlayer and Audacious!?? This doesn't make much sense, if the packages are obsolete, why are the latest versions the same? And why list them if they are still used by many applications?

You have probably got a bad Repository in your setup, do a Reload and see if there are problems.

---

### Post by oldos2er on 2010-09-26
'Local or obsolete' refers to packages which you have built yourself (local) or which are no longer in the repositories listed in /etc/apt/sources.list, or which are in a repository you removed from that list (obsolete in both cases).

---

### Post by veggen on 2010-09-29
Ok, make sense. Thank you :)

---

