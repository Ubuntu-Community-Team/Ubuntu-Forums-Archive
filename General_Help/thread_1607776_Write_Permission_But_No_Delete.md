---
title: "Write Permission But No Delete?"
date: 2010-10-28
forum: General Help
---

### Post by csharpplus on 2010-10-28
I am a newbie, so thanks in advance for any help.

What is the best way, in terms of permissions, to allow a user to **write to a folder** (meaning, the user is allowed to create new files) BUT prevent from the user to delete files in that folder?

Is there a way to achieve this?

---

### Post by csharpplus on 2010-10-28
I am a newbie, so thanks in advance for any help.

What is the best way, in terms of permissions, to allow a user to **write to a folder** (meaning, the user is allowed to create new files) BUT prevent from the user to delete files in that folder?

Is there a way to achieve this?

---

### Post by scinerd on 2010-10-28
I think you want to do something like use the sticky bit on the directory. 

[http://linux.die.net/man/1/chmod](http://linux.die.net/man/1/chmod)

  This will limit users from deleting each others files.  The other options is to write a script that locks files down as they come into the area. 

  Might have a better solution, can you give more details on why you want to do this?

---

### Post by drz4007 on 2010-10-28
Check this out [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by karthick87 on 2010-10-28
ACL will do this.

---

### Post by s.fox on 2010-10-28
Threads merged. Please do not create duplicate threads. Thank you.

---

