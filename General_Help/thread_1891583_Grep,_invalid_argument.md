---
title: "Grep, invalid argument"
date: 2011-12-05
forum: General Help
---

### Post by lumbricus on 2011-12-05
I'm also encountering the same behavour with grep and folders. Very strange: it seems to be connected to home directory encryption.

When I run ```
grep somthingToSearch /tmp
``` grep doesn't return anything (and this is what I expected because there is nothing to find). But ```
grep somthingToSearch /home/user
``` ...returns: ```
grep: /home/user: Invalid argument
```

Note that "user" is the user name of the user currently logged in and the folder is enrypted usign Ubuntu's default method of home directory encryption. And the error message seems to be connected to the encryption. On another ubuntu machine without home folder encryption grep isn't returning any error.

---

