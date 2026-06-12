---
title: "Partial upgrade to 10.10"
date: 2010-10-16
forum: General Help
---

### Post by Robbyx on 2010-10-16
I can not complete the aborted upgrade because the update manager can get an exclusive lock. 


The update manager says:

> 
Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first. 

> sudo dpkg --configure -a

Status database is locked by another process.

Synaptec is not loaded. Htop shows nothing about apt-get.

The upgrade froze 5 mins before the end. I dare not restart the machine until I have repaired the update. I can not complete the partial update because of the lock.

How do I trace the lock and turn it off.

---

### Post by Robbyx on 2010-10-16
This solved it:

sudo fuser -vki /var/lib/dpkg/lock

---

