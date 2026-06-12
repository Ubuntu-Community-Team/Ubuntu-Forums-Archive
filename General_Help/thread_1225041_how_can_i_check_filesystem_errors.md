---
title: "how can i check filesystem errors"
date: 2009-07-28
forum: General Help
---

### Post by sububtu on 2009-07-28
how can i check "filesystem" errors using fsck command.?
the problm is - the file system is mounted, how can i free it and run fsck,
im tried this command but i got this msg-
"WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage."

---

### Post by nikhilk on 2009-07-28
> **sububtu said:**
> how can i check "filesystem" errors using fsck command.?
the problm is - the file system is mounted, how can i free it and run fsck,
im tried this command but i got this msg-
"WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage."

Yes, you must NEVER run fsck on a mounted partition. Which partition are you trying to scan? If it is the /home partition you can run fsck from single user mode.

---

### Post by sububtu on 2009-07-28
this system returned an error msg that "fsck failed" and must run fsck manually (without using -p -a ), then i had done it manually without these arguements..
i got a huge list of errors,which asks user confirmation for correction(y/n),that was a through checking of root for more than 4/5 mins, , ,, somebody had hit "No" for series of confirmations(probably the students) so it is incomplete, and i need to run fsck fo the entire FS

---

### Post by nikhilk on 2009-07-28
> **sububtu said:**
> this system returned an error msg that "fsck failed" and must run fsck manually (without using -p -a ), then i had done it manually without these arguements..
i got a huge list of errors,which asks user confirmation for correction(y/n),that was a through checking of root for more than 4/5 mins, , ,, somebody had hit "No" for series of confirmations(probably the students) so it is incomplete, and i need to run fsck fo the entire FS

In this case I suggest running Ubuntu from a live-CD. First ensure that none of the installed Ubuntu system's partitions are mounted and then fsck from the live-CD.

---

### Post by prshah on 2009-07-28
> **sububtu said:**
> how can i check "filesystem" errors using fsck command.?

Boot to the command prompt, give the below command and restart; a filesystem check will be triggered```
sudo touch /forcefck
```

---

### Post by sasho_zl on 2009-07-28
Run the the system in single user mode with the command **sudo init 1**. In the menu there is an option for scanning the filesystem ;)

---

