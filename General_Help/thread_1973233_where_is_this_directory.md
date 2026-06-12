---
title: "where is this directory?"
date: 2012-05-04
forum: General Help
---

### Post by TXbirder on 2012-05-04
I have run a backup (I think) for the first time.  I have been following instructions in Help.  In the how-to, item 7 says, in part: Your backup will be placed as directory into /var/backup. 

Where is this directory and how do I get to it?  I want to copy the back up to a flash drive.

John in Houston

---

### Post by papibe on 2012-05-04
Hi TXbirder.

Which version are you running? 10.04? 12.04?
Do you refer to the Helps documents that are launched by F1?
Or to the tutorials and wikis on help.ubuntu.com?

Regards.

---

### Post by PeterP24 on 2012-05-04
> **TXbirder said:**
> I have run a backup (I think) for the first time.  I have been following instructions in Help.  In the how-to, item 7 says, in part: Your backup will be placed as directory into /var/backup. 

Where is this directory and how do I get to it?  I want to copy the back up to a flash drive.

John in Houston

On my system (11.04) I go in the Places -> Computer then double click on File System then /var directory.

---

### Post by TXbirder on 2012-05-04
I'm running 10.04.  The help I used is what I get when I click the blue dot with the question mark on the bar at the top of the screen.

---

### Post by wojox on 2012-05-04
Ctrl+Alt+T opens a termnal.
Move into the directory:
```
cd /var/backup
```
Lists all files that are in there.
```
ls -al
```

---

### Post by TXbirder on 2012-05-05
I found it. Thanks.

---

