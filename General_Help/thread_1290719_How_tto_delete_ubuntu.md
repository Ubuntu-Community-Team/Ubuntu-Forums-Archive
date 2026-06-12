---
title: "How tto delete ubuntu"
date: 2009-10-13
forum: General Help
---

### Post by kenilworthkid on 2009-10-13
How do I remove ubuntu and the bootloader.  I tried (e)dit and deleted the lines for ubuntu, as soon as I restart they're back.  What is the file name I need to edit to restore my normal boot?  It's not usable, all I want is to remove it.  Someone please tell me the magic words to get my normal bootloader back.

---

### Post by chandru155 on 2009-10-13
Boot with your Xp Cd and select Repair, then choose your windows drive(i think its 0 or 1 for c drive), i forgot,then give your Admin password,then type FIXMBR in command prompt. thats all, when you restart,your old Xp boot option will be restored

---

### Post by kenilworthkid on 2009-10-13
> **chandru155 said:**
> Boot with your Xp Cd and select Repair, then choose your windows drive(i think its 0 or 1 for c drive), i forgot,then give your Admin password,then type FIXMBR in command prompt. thats all, when you restart,your old Xp boot option will be restored

Thank You!  It's 2000 Pro, but the process should be similar.

---

### Post by cwbar_1 on 2009-10-13
_Before_ you follow chandru's directions, you need to go into disk management for xp and reclaim the Ubuntu partition.  I do not remember the procedure for XP. Search with google.

[https://lists.ubuntu.com/archives/ubuntu-users/2004-December/016731.html](https://lists.ubuntu.com/archives/ubuntu-users/2004-December/016731.html)

Scroll to the bottom of the post for directions......

---

### Post by kenilworthkid on 2009-10-14
All done, thanks to all who replied

---

