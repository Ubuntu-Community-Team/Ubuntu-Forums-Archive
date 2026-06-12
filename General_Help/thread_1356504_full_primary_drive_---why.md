---
title: "full primary drive ---why?"
date: 2009-12-16
forum: General Help
---

### Post by Dan Z on 2009-12-16
Running 8.1
Primary drive is 66GB. Normally it had 28 GB free. Now it is full. SO 28 GB got filled, I know not how. I did not fill it.

If I look at the contents of the drive it does not show what the 28 GB consists of. So the 28 GB is a mystery.

Any tips on how to find the problem and restore my empty space?

Thanks Dan

---

### Post by akakingess on 2009-12-16
Have you tried just booting from a LiveCD and checking it, and if it still says that try running "fsck" or "testdisk" on it and see if it is just drive partitioning damage?

---

### Post by Grenage on 2009-12-16
I would be suspecting log files, how big is /var/logs?

---

### Post by akakingess on 2009-12-16
Just a question, does about 4 MBs seem right for the size of /var/log?

---

### Post by Grenage on 2009-12-16
That's about right for a healthy system; mine is the same.

---

### Post by akakingess on 2009-12-16
Thanks for the quick response, and Dan Z, if you need to know how to find out the size of /var/log just let us know, but at least now you have something to look for, and thanks again Grenage.

---

### Post by plucky on 2009-12-16
> **Dan Z said:**
> Running 8.1
Primary drive is 66GB. Normally it had 28 GB free. Now it is full. SO 28 GB got filled, I know not how. I did not fill it.

If I look at the contents of the drive it does not show what the 28 GB consists of. So the 28 GB is a mystery.

Any tips on how to find the problem and restore my empty space?

Thanks Dan

Check this [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573) thread


Good Luck

---

### Post by Dan Z on 2009-12-17
ok found problem. 31 GB of backups found its way to /media instead of the the external drive. 

Found using the commands in HOW TO:Lost disk space.

Thanks all for help. Dan

---

