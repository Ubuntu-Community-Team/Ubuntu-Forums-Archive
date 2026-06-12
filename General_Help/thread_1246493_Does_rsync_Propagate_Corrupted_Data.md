---
title: "Does rsync Propagate Corrupted Data?"
date: 2009-08-21
forum: General Help
---

### Post by cjsheets on 2009-08-21
Hi,

I've been searching for a while and was hoping someone cold shed some light on this question for me.

I've been using rsync in my backup schemes for some time now and one of my file servers recently decided it didnt like larger (1Gb-2Gb) files and it corrupts them every now and then.

I use rsync to backup data from the fileserver and i was wondering if a file becomes corrupted on the server, does rsync propagate that (incorrect) change to the backup copies?

My rsync call is nothing fancy, usually a basic rsync -ar /../.. /../..  
or sometimes -br

---

### Post by XCan on 2009-08-22
Yes. rscyn can't judge whether a file is corrupt or not, it will only compare the files and apply changes made to the oldest file from the newest file.

---

