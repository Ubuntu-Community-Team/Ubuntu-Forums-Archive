---
title: "Déjà Dup to external hdd stopped working after 11.10 update"
date: 2011-12-19
forum: General Help
---

### Post by Dammerl on 2011-12-19
Dear All,

I had been using déjà dup to back up my laptop all summer long successfully. I backed up to an external hard drive (Dreambox/Enigma), via the local folder option, which pointed at the mounted drive (root user; automount at startup). I all worked fine until I updated to 11.10 a few weeks back when the backup stopped. It started with the scanning and usually also created some files but eventually stopped with an "permission denied" error. I have been searching the web but so far could not find any pointer. 
I have now also tried the SSH option, but here déjà does not even start.

I have no idea where to start looking, whether déjà was updated as well, or whether any other installation may have caused this issue. Any help would be appreciated. Please also let me know which information would be useful (and how to get it - I just recently switched to Linux).

Looking forward to all your help!
Tom

---

### Post by ppanish on 2012-06-21
I've filed a bug on this problem: [https://bugs.launchpad.net/ubuntu/+source/deja-dup/+bug/1016012](https://bugs.launchpad.net/ubuntu/+source/deja-dup/+bug/1016012)

It appears permissions on numerous files have changed so that access is only possible as root. I don't know whether this problem would best be solved by giving root permissions to the backup process, or granting read access for most of the files in question.

---

