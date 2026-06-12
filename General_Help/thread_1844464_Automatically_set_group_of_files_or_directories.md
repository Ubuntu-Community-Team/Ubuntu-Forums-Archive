---
title: "Automatically set group of files or directories"
date: 2011-09-15
forum: General Help
---

### Post by fenix88 on 2011-09-15
Greetings!

Is there a way to automatically set the group of a newly created file or directory so that I don't have to call chgrp manually? I tried calling chgrp after umask in /etc/profile, but I don't think it works that way? Or am I just missing something?

---

### Post by fdrake on 2011-09-15
have you tried acl - Access Control Lists?

---

### Post by dcstar on 2011-09-15
> **fenix88 said:**
> Greetings!

Is there a way to automatically set the group of a newly created file or directory so that I don't have to call chgrp manually? I tried calling chgrp after umask in /etc/profile, but I don't think it works that way? Or am I just missing something?

AFAIK creating new groups/files anywhere will use the Main Group of the user account that creates the object, so you will have to manually set the Group if it needs to be different.

---

### Post by sisco311 on 2011-09-15
If the SGID bit is set on a directory then any new files and directories created within the directory will inherit the group of that directory. See: [http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by fdrake on 2011-09-15
a combination of setgid and ACL should do what you are looking for
[http://brunogirin.blogspot.com/2010/03/shared-folders-in-ubuntu-with-setgid.html](http://brunogirin.blogspot.com/2010/03/shared-folders-in-ubuntu-with-setgid.html)

make sure you apply the permissions to a specific group since!

---

### Post by SeijiSensei on 2011-09-15
If you want your user account to use a specific group by default, the quickest solution is to edit (as root) your entry in /etc/passwd.  

```
seiji:x:1000:1000:SeijiSensei,,,:/home/seiji:/bin/bash
```

The first "1000" is my user ID; the second one is my group ID.  If you want this account to routinely use a different group by default, change the second numerical entry to the group ID to which you want to belong.  Look at /etc/group to see the groups and their gid's.  For instance, making your default group 33 and making /var/www group-writable would enable you to edit files served up by the Apache webserver.

---

