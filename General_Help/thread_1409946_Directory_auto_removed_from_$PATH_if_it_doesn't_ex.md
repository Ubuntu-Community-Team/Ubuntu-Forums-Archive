---
title: "Directory auto removed from $PATH if it doesn't exist?"
date: 2010-02-18
forum: General Help
---

### Post by djeyewater on 2010-02-18
I have MySQL installed in a non-standard location, and it has always worked okay by starting it with ```
mysqld_safe --defaults-file=/path/to/mysql/my.cnf
```
But yesterday I renamed my mysql directory to mysql-old, and installed a new version of mysql to my mysql directory. I couldn't start the new version of mysql, and found the problem was with apparmor blocking /usr/sbin/mysqld. Looking at my PATH, I found it didn't contain the path to the bin directory of my mysql installation, which explains why /usr/sbin/mysqld was being executed and blocked by apparmor instead of my mysql installation being executed.

Since my mysql installation worked okay previously, I can only assume that $PATH previously did contain the path to my mysql bin directory, and that some automatic process removed it from PATH between the time I renamed my mysql directory to mysql-old and the time that it took to  install the new version of mysql.

Is there some automatic process that cleans non-existing paths from the PATH environment variable?

Thanks

Dave

---

