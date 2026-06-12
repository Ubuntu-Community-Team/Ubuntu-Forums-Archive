---
title: "how to change file permissions?"
date: 2009-08-01
forum: General Help
---

### Post by kaptain0 on 2009-08-01
Is there a way to change file permissions in the usr/share folder, or any of the file system, to something other than root?
 
My big problem is trying to copy files into the filesystem but it says I don't own those files. i know you can't login as root, but I'm not a fan of sudo.
 
jaunty, btw
 
Thanks

---

### Post by wojox on 2009-08-01
open a terminal:

```
gksudo nautilus
```

It will open your file browser and let you copy away.

---

### Post by kaptain0 on 2009-08-01
Thanks!
 
how is gksudo different from sudo, btw?

---

### Post by wojox on 2009-08-01
It will open up a graphicel app. Read here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

