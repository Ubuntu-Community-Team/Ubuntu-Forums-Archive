---
title: "Cannot uninstall phpmyadmin"
date: 2006-03-30
forum: General Help
---

### Post by Roxxor on 2006-03-30
Hi!

I'm trying to uninstall PHPMyAdmin.

I have translated the console text below from swedish to english.

I get following error:
```

roxxor@laptop:~$ sudo apt-get remove phpmyadmin
.....
.....
Following packages will be removed:
  phpmyadmin
0 upgraded 0 installed 1 to be removed och 0 not upgraded.
E: Could not get the lock /var/cache/apt/archives/lock - open (11 Resources temporarly unavailable
E: Could not retrive the folder

```

What's wrong?

---

### Post by localzuk on 2006-03-30
Do you have any other package management apps open? If so, quit them and try running the command again. If not run ```
sudo rm -f /var/cache/apt/archives/lock 
``` to remove the lock file (a lock file states that another application is making use of that resource, so if no other app IS making use of it, then it can be deleted) and try again.

---

### Post by Roxxor on 2006-03-30
Ok. I removed the lock file but now I get this in the Synaptic console (translated from Swedish):
```

Removing phpmyadmin...
 /var/lib/dpkg/info/phpmyadmin.prem: line 12: db_get: command not found underprocess pre-removal script error code 127
Could not remove
phpmyadmin
```

---

