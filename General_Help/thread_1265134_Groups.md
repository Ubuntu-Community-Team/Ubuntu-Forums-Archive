---
title: "Groups?"
date: 2009-09-13
forum: General Help
---

### Post by RFXCasey on 2009-09-13
Can anyone tell me how I find out what rights a group has? And why are there so many listed? This is way lame.

---

### Post by hwttdz on 2009-09-13
I don't think groups have any rights, rather users which belong to a group can have rights. When you look at file permissions, i.e. ls -l, you see 3 sets of permissions

fileowner/groupowner/everyoneelse

So if a file is owned by bugs, and the group is toons, and the permissions are

rwx, rx, r

Then bugs can read, write or execute, anyone in the toons group can read or execute, and everyone else can only read.

---

