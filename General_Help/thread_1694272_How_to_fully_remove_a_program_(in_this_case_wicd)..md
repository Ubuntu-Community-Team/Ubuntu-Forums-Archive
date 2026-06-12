---
title: "How to fully remove a program (in this case wicd)."
date: 2011-02-24
forum: General Help
---

### Post by zozza on 2011-02-24
Hello, 

I had wicd installed.  I removed it with sudo apt-get remove wicd.  I have also used sudo apt-get purge wicd.

Results:

Package wicd is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

Locate wicd reveals hundreds of files.  

Whereis wicd reveals:

wicd: /usr/sbin/wicd /etc/wicd /usr/share/wicd /usr/share/man/man8/wicd.8.gz

How can I remove wicd fully?

Thanks

---

### Post by zenwalker on 2011-02-24
Are you sure you didnt install wicd using a source? If it has been installed by dpkg or apt-get then it sure can remove it.

---

### Post by WorMzy on 2011-02-24
The database that locate uses may not have updated yet, which may be why it's still telling you about the files in question.

Run
```
sudo updatedb
```
to force the database to update, then run the search again.

---

