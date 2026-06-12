---
title: "javaldx in OpenOffice.org 3.1.1 eating all my memory"
date: 2009-09-04
forum: General Help
---

### Post by Irihapeti on 2009-09-04
I'm not sure if this is the right place to ask this, but I'll try anyway...

I've upgraded to the latest OpenOffice.org from the OpenOffice.org website.

I also upgraded Java from 1.6u15 to 1.6u16. I'm running Ubuntu 8.04

Twice now, I have opened OpenOffice.org writer, while I had another Java-based program active, and javaldx has proceeded to consume all my memory (1.4 GB) plus half of the swap (1GB). I've been able to kill javaldx and the system becomes usable again.

The only thing is, it then happens every time I open writer, even if I've closed everything else and rebooted. Completely removing and reinstalling OpenOffice.org doesn't help. The only cure has been to reinstall my system from a backup - thank goodness I had one! (and also a separate /home partition) But doing that gets old rather quickly. I've not upgraded the Java after the second reinstall.

Does anyone know what's going on here? Is there any way of fixing the problem without needing to reinstall the system? Is the problem with OpenOffice.org itself, or with the Java upgrade? 



Thanks

---

### Post by Hagar Delest on 2009-09-04
Try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

---

### Post by Irihapeti on 2009-09-04
Thanks for the suggestion. I actually used it to solve a problem on another computer. 

It hasn't helped on this machine, though. I renamed the old profile folder, restarted OpenOffice.org and the problem happened again! Evidently, it's not the latest Java, since I didn't upgrade it.

I'm thinking I may need to reinstall. I am having some other trouble with OpenOffice.org - the dictionary .debs won't run their pre- and post-install/remove scripts when I try to install or remove them.

It's only happening on my desktop machine. I have Ubuntu 8.04 and OpenOffice.org 3.1.1 on an EeePC 900 and it's working fine. So maybe something somewhere has got corrupted. Perhaps I should blame my son for trying out all kinds of games on my desktop PC :)

---

### Post by Hagar Delest on 2009-09-05
> **Irihapeti said:**
> I'm thinking I may need to reinstall. I am having some other trouble with OpenOffice.org - the dictionary .debs won't run their pre- and post-install/remove scripts when I try to install or remove them.
What do you mean? Don't use the install script provided, use your package manager. See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by Irihapeti on 2009-09-05
> **Hagar de l'Est said:**
> What do you mean? Don't use the install script provided, use your package manager. See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Sorry I didn't make myself very clear the first time.

I always use the method shown in your link to install. I remove the previous version through synaptic before installing the latest one. Once the .debs are installed, some configuration stuff happens and this is where apt/dpkg hangs. I believe that there's a script, included in the .deb package, that gets run at this time.

As I'm not having this problem on my other two systems (both Ubuntu 8.04), I'm beginning to think that something's got messed up on this one.

---

