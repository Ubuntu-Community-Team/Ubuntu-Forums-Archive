---
title: "Password protecting folders"
date: 2009-06-29
forum: General Help
---

### Post by Lluraeden on 2009-06-29
Hi I was wondering if there is a way to make a specific folder password protected, so users would have to enter an administrator password whenever they wanted to open a this folder.

---

### Post by dtoronto on 2009-06-29
yes, just make the folder user as root.

```
$sudo chown -R "folder name"
```

This will set the owner of the folder as root requiring root access to edit.

---

### Post by t4thfavor on 2009-06-29
change the permissions, and owner of the file, or right lick, and select Encrypt. This should get youthe desired effect. you could also try moving them to an unmounted hdd, regular users can't mount disks wwithout admin passwords.

---

