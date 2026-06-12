---
title: "incron not deleting files"
date: 2011-08-29
forum: General Help
---

### Post by c8a7w on 2011-08-29
having a weird problem with incron

setup is to run a script that uploads file to a machine off site so incron runs the following

```
/home/user/scripts/syncscript.sh IN_CREATE $@$# && rm $@$# 
```

only issue is the files don't get deleted, if i execute the command as taken from /var/log/syslog it executes correctly.

permissions are 644, my assumption is the operation is executed as the user so this is not a problem. 

Am I incorrect in this assumption or is there another problem?

---

