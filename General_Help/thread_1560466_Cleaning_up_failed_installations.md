---
title: "Cleaning up failed installations?"
date: 2010-08-24
forum: General Help
---

### Post by oyouareatubeo on 2010-08-24
I was installing a few programs when my computer froze, I rebooted, and the installations never finished. I didn't log in to ubuntu for several days, and forgot the exact programs that I was trying to install. Now when I try to open up Synaptic Package Manager, I get this error:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I can't install certain programs, etc.  Something is screwed up.  I think it has to do with the failed installations.  My question: How do I clean up these failed installations.  I'm kind of a linux noob, so some help would be appreaciated... I'm trying to fall in love with her!  Thanks.

---

### Post by oldfred on 2010-08-25
From a terminal run all these commands, The # are comments to explain a little and you need to add sudo before every one of these.

#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

