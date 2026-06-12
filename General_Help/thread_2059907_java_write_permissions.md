---
title: "java write permissions"
date: 2012-09-19
forum: General Help
---

### Post by neville9763 on 2012-09-19
i have a problem that is driving me nuts and there must be a simple answer which i can't see.

i have installed some custom java software as root. part of the install is to create a number of subdirectories - which are owned by root - into which text files eg. log files get written.

during the install i change the permissions on the subdirectories so that all ie. 'a' has read, write permissions (a+rw, a=rw - i have tried a few permutations).

i run the software as a normal user (java -jar xxx.jar) i am not able to create/write files in the subdirectories as i keep getting 'permission denied'. if i run as root (sudo java -jar xxx.jar) the files are written without any issue.

what am i missing?

tia

---

### Post by vandorjw on 2012-09-19
Let say you have your java program installed here:
> 
/opt/neville9763_java/bin

Imagine your user name is neville9763

This is how to solve permisions.
```

sudo chown -R neville9763 /opt/neville9763_java/
sudo chgrp -R root /opt/neville9763_java/
sudo chmod 775 -R /opt/neville9763_java/

```

These 3 commands set:
1) you to the owner of all files in the folder neville_java
2) root is the group that the files belong to..so anyone in group root will also be able to modify files
3) sets the permissions for owner to rwx, group to rwx, and others to rx

---

