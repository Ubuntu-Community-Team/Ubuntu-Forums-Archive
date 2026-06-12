---
title: "Log permission denied issue"
date: 2012-04-05
forum: General Help
---

### Post by mohanradhakrishnan on 2012-04-05
When I try to run a certain command related to Django 'syncdb' for installation of graphite I get an error. Now as a means of debugging that issue I would like to know how to turn on logging to figure out which folder's permission is causing this problem.
 
The other relevant thread is [http://ubuntuforums.org/showthread.php?t=1948956](http://ubuntuforums.org/showthread.php?t=1948956)
 
Windows system logs show which folder and which user are involved when the file system is accessed.
 
Can I get some help here ? If I know from the logs exactly what folder is being accessed and which user is involved I might be able to debug the issue.
 
**Update :**
 
I was able to view the auth.log using System Log Viewer to find out which user is running a command. Trying to find which folder or file is involved.
 
Mohan

---

### Post by codemaniac on 2012-04-05
Please ensure read permission to appropriate users and groups for viewing auth.log . 
Can't you simply grep the necessary information related to your issue from auth.log ?

---

### Post by mohanradhakrishnan on 2012-04-05
I have been able to view the auth.log. No problem.
 
It is just that it is a python django issue. Should really pursue it with the Django users unless you have some idea about this. It is part of a graphite installation.
 
Thanks.

---

