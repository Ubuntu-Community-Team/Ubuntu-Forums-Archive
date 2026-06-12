---
title: "Not Allowed to Read Drive"
date: 2006-05-21
forum: General Help
---

### Post by cssutto on 2006-05-21
I have a Maxtor external drive on which I store backups.

It is partitioned into three.

Two of the three partitions are exclusively for W2K backups.

The third partition is where I store linux backups, made by Simple Backup.

Occasionally I like to look at this partition to see that the backups were made on scheduel, which I have been able to do.

Recently I have been denied the permission to even look at it.

I can look at if when running W2K, but not when running Ubuntu.

This is the message I receive:  
Error: directory /media/usbdisk is not empty
Error: could not execute pmount

However, when I go to the file browser and look at it, it tells me that usbdisk is empty.

I had this happen once before and found a work around, but I tried so many things that I can not remember which one worked.

In any case, I would like a one time fix it now and for all.

CSSJR

---

### Post by cssutto on 2006-05-21
I recall now that I changed to root and got +rw permissions and then it worked.

Then I got to thinking that it was -rw for a reason, so I cnanged it back to be safe.

So what is the permanent fix?

I just changed it again to +rw and found that it has not done an automatic backup for a week.  It is set to back up every day at 22:00.

Does this have to do with the permission problem?

Also, this morning I asked it to back up manually.  It tells me that it is doing number ##### in the background, but then does nothing.

I would like to get this resolved.

CSSJR

---

