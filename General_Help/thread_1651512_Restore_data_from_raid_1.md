---
title: "Restore data from raid 1"
date: 2010-12-23
forum: General Help
---

### Post by Taak on 2010-12-23
I have two disks from a old computer (now it doesn't exist anymore). They were in raid 1 with this configuration:
 
```

 
----------------
| disk 1 | disk 2 
----------------
|        OS         
----------------
|         |         
| raid 1  | raid 1
|         |         
----------------
 

```
 
There is probably an error in one of the two disks, however raid 1 should allow we to restore data.
 
So now I can physically mount this disks on a machine with ubuntu (ubuntu is on another disk). My question is: how can I restore data from disks?
 
I'm searching for a guide to do this. I think that using mdadm is not enough.
 
Have you ever done this before? Do you now any good program/guide to do this?
 
Thank you

---

### Post by psusi on 2010-12-23
What do you mean by "restore"?  I can't make sense of that word in this context.  Usually you restore your data to the disk from some backup medium, but you seem to already have the data on the disk.

---

### Post by Taak on 2010-12-23
Yes the data are on the disks but probably one disk is corrupted.

I simply want copy my data from the raid 1 mirror to another new disk.

---

### Post by psusi on 2010-12-23
Then mount the good disk and copy away.

---

