---
title: "external hd problem"
date: 2010-10-20
forum: General Help
---

### Post by salmonila on 2010-10-20
hi,I have a 250gb external hd with fat16 file system when I formated it to ext4 I found a folder named (lost+found) with the same volume of the data on it when it was formated ,I don't need that data but the problem that I can't delete the folder or even access it ,I only got a message ( you don't have the wright permission to access that folder),so what can I do the folder is taking 50gb

---

### Post by Hippytaff on 2010-10-20
try using sudo
 
```

sudo cd /path/folder

```
 
or
 
```

sudo rm /path/folder

```
 
to delete the folder...or change the permissions of the filder with chmod - [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

