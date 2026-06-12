---
title: "advanced permissions"
date: 2011-01-28
forum: General Help
---

### Post by Robx610 on 2011-01-28
Here is my scenario:

I have a file server running 10.04.

I have a user that belongs to 2 groups (users is the primary and IT is the secondary). I have permissions set up so that this user and other users that belong to the IT groups can read/write files and others have no permissions whatsoever. I have also set the umask to 0007 so that any files created have the effective permissions. My concern is this: since my primary group is users, is it possible for me to create files with the owner group IT for only this specific folder ?

Thanks in advance.

---

### Post by sisco311 on 2011-01-28
Yes. You have to set the sgid bit on the directory. See:
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by Robx610 on 2011-01-28
Perfect. Thank you so much.

---

