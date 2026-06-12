---
title: "How do I tar into tar.bz2 a locked backup directory from the simpleconfig backup prog"
date: 2010-03-12
forum: General Help
---

### Post by Lukasz Tarkowski on 2010-03-12
How do I tar into tar.bz2 a locked backup directory from the simpleconfig backup program? The backup directory is located in /home/lukasz/Downloads/backup/

---

### Post by spiderbatdad on 2010-03-12
change the permissions on the directory.
list the files with:
```
ls -al /home/lukasz/Downloads/

```
Use sudo chown user_name:user_name directory_name to make yourself owner of the directory, and sudo chmod -R 755 directory_name to edit default read, write,execute permissions.

---

