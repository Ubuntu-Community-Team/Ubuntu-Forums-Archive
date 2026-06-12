---
title: "Passwd delete -- Account recovery"
date: 2012-09-18
forum: General Help
---

### Post by tabennett on 2012-09-18
Hello.

Upon deleting the /etc/passwd file (without knowing what it would do -- I'm not doing that again) and realizing that I had boot errors, I booted up into an Ubuntu 12.04 Live USB and copied the passwd file on it into the /etc directory of my passwd-less partition. Whenever I booted into Ubuntu, I was allowed through, but am only allowed in a Guest account, with my previous account not showing up at all. Also, whenever I try and access the /home directory, I am informed that I do not have the permission to access it.

If anyone can help me, or can direct me to a thread where a problem like this has already been solved, I will be grateful. Thank you.

---

### Post by shadedpixel on 2012-09-18
It may just be easier to re-install, although this is not ideal if you have alot of data on the system.

---

### Post by steeldriver on 2012-09-18
It should be possible to re-add the users (useradd or adduser) from the recovery console, specifying the existing home dirs. You may need to tweak things to make sure the UIDs / GIDs / home dir ownerships all line up - good luck

---

