---
title: "Seach locate database for external drive while drive offline"
date: 2009-07-19
forum: General Help
---

### Post by albe.mann on 2009-07-19
On Windows I used the locate clone Locate32 for quickly searching my external drives while they were off. I have so far not been able to do the same with Ubuntu. I have created a database of the external drive with
```
sudo updatedb -o external.red.db -U /media/external%red
```And I have added this database file to LOCATE_PATH.
Unfortunately, locate only finds files on the external drive when it is online. How can I search the database when the indexed drive is offline?

Looking forward to your help.

---

