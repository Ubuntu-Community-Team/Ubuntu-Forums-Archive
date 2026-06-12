---
title: "Changing default file rights on creation"
date: 2011-02-17
forum: General Help
---

### Post by alzorz on 2011-02-17
My problem is that I want newly created files to be 775 but they are 644 according to ls -l tho user that created can still write to file while other user in same group can't.

Current umask is 002.

Can't findout how to get newly created files to be 775. What should i do make all new files created by a user to be 775?

---

### Post by tinkernutfan on 2011-02-17
[bump] i want to know to

---

### Post by Morbius1 on 2011-02-17
You've got two completely different questions:
> My problem is that I want newly created files to be 775I don't think you can. New files start out in life as 666 and then the umask is automatically applied. So even with a umask = 000 the best you're able to achieve is 666. You can create new directories with 775 because they start out as 777 before umask.

> but they are 644 according to ls -l tho user that created can still write to file while other user in same group can't.

Current umask is 002.2 problems with that statement:

(1) If you have a umask of 002 and it still creates a new file with 644 instead of 664 then there's a problem somewhere. Did you logoff and login again after changing the umask?

(2) Changing the umask has nothing to do with the other users ability to write to that file because it will not save to the same group.

userA's file will save as owner:group = userA:userA and
userB's file will save as owner:group = userB:userB

---

### Post by alzorz on 2011-02-18
Thanks for the answer. When i checked rights on creation again now they were 664.

---

### Post by EifleMan on 2011-02-20
Is it possible to define different default rights for files and directories on creation?

---

### Post by Morbius1 on 2011-02-21
> **EifleMan said:**
> Is it possible to define different default rights for files and directories on creation?
For ntfs or fat32 partitions - yes
For specific directories on Linux partitions using bindfs or ACL - yes
For Linux partitions covering all directories - I don't think so.

---

