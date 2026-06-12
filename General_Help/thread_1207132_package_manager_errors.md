---
title: "package manager errors"
date: 2009-07-07
forum: General Help
---

### Post by pjp14180 on 2009-07-07
Hi I attempted to install some apps today using synaptic, I got the following errors  'E:Malformed 3rd word in the Status line,  E:Error occurred while processing mysql-common (UsePackage2),  E:Problem with MergeList /var/lib/dpkg/status,  E:The package lists or status file could not be parsed or opened.'  I found the malformed word and edited the status file and corrected it.  I then continue to get errors and finally got the following errors  Reading package lists... Error! E: Encountered a section with no Package: header E: Problem with MergeList /var/lib/dpkg/status E: The package lists or status file could not be parsed or opened.  How can I fix this, I probably made things worse by trying to fix the status file.  I would like to be able to clear this up but am at a loss as to how.  Thanks.

---

### Post by CatKiller on 2009-07-08
What happens if you rename that file to status.backup and then run apt-get update?

---

### Post by Soul-Sing on 2009-07-08
cd /var/lib/dpkg
mv status status-bad
cp status-old status

apt-get update

---

### Post by pjp14180 on 2009-07-08
I tried this and found I needed a status file so I copied an older file to status and ran apt-get- update.  This worked I can now apply the latest updates.  Thanks for the help
Paul

---

