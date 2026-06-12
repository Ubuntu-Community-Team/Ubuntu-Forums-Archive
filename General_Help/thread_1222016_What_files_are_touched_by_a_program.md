---
title: "What files are touched by a program?"
date: 2009-07-24
forum: General Help
---

### Post by quaternion on 2009-07-24
I have a program that I need to understand better.  I want to know when I run it what files are accessed?

---

### Post by philcamlin on 2009-07-24
try rinning it in terminal and stuff 

ie: if i ran gparted id go sudo gparted

---

### Post by quaternion on 2009-07-24
Thank you but I am looking for a log.
Something more like:
File a was accessed by user X at [timestamp]
...
File z was accessed at user X at [timestamp]

What would be even better is one that works in real time and provides filters (to remove swap space access and filter by particular user).

I just want file access by my user.  I want to know if there are accesses outside of a certain set of folders.  If I could just get raw file access logs I can get the data I need.

---

### Post by Whiffle on 2009-07-24
I think you might be looking for this:

[http://www.cyberciti.biz/tips/linux-audit-files-to-see-who-made-changes-to-a-file.html](http://www.cyberciti.biz/tips/linux-audit-files-to-see-who-made-changes-to-a-file.html)

---

### Post by quaternion on 2009-07-24
Thank you very much that looks very promising.  Linux is amazing.

---

