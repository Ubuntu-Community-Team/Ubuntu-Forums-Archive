---
title: "Maverick and Mysql"
date: 2010-10-23
forum: General Help
---

### Post by rew222 on 2010-10-23
I have two Ububtu 10.04 systems. I upgraded one of them from 10.04 to 10.10. Mysql version is now 5.1.49. After upgrading, a mysql script that uses 'LOAD DATA INFILE..." started throwing errors, file not found and can't stat file. I searched around the net and found it to be a rights issue. The weird thing is that the file is sitting in /tmp, and it worked fine before I upgraded. I tried to chmod 755 the file, I tried load data LOCAL infile, I tried copying the file to my home directory, nothing worked. I finally had to su to root, and even then had to copy the file to /var/lib/mysql/<database name> for it to finally work.
 
On the other 10.04 system, the same script works fine with Mysql 5.1.41.
 
Is this a bug?
 
TIA,
Bob/

---

### Post by rew222 on 2010-11-29
I finally was able to isolate the problem to apparmor. To fix this issue I had to modify /etc/apparmor.d/usr.sbin.mysqld and add the following lines to the list of paths:
 
/tmp/ r,
/tmp/* rw,
 
You must su to root to make the changes.
 
Regards,
Bob/

---

### Post by kanishkdudeja on 2010-11-30
great. Congrats. Mark the thread as solved.

---

