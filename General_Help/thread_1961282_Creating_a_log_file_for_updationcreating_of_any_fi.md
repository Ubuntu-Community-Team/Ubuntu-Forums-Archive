---
title: "Creating a log file for updation/creating of any file in ubuntu"
date: 2012-04-19
forum: General Help
---

### Post by vishrav on 2012-04-19
Hi

i need to update a file, every time a file present in ubuntu file system gets written/created/updated. One method i have thought is to monitor open system call for write permission. Also it should be event driven like if any such activity is done it is automatically detected.
But i am unable to do it. Please suggest some other method or a solution to the above method.


Thanks in advance
Vishrav

---

### Post by conradin on 2012-04-19
doesn't syslog do something like that already?
are you asking that for every file on the filesystem or for a specific set of files?

---

### Post by codemaniac on 2012-04-19
Can you use find command to find the newer created , modified , accessed files and then do an update in some log file with details that which files have been changed .You can then list your find commandline as a cron entry to check it in certain intervals .

---

