---
title: "Change permissions to /var/www"
date: 2011-04-30
forum: General Help
---

### Post by haydenh on 2011-04-30
After changing the ownership of the /var/www directory I am now getting a 403 Forbidden message. I tried changing it back to root but am still receiving the same message.

Any help would be much appreciated!

---

### Post by haydenh on 2011-04-30
```
sudo chown -R root:root /var/www
```
```
sudo chmod -R 755 /var/www
```

These commands seemed to make it work. Is this correct?

---

### Post by haydenh on 2011-04-30
When creating new files within the folder they are not given the proper permissions. How do I set permissions to newly create/uploaded files (preferably with the lowest permission need to view)?

---

