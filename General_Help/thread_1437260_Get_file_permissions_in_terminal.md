---
title: "Get file permissions in terminal"
date: 2010-03-23
forum: General Help
---

### Post by johngreth on 2010-03-23
Is there a command I can use to get the permissions of a folder in a terminal? Everything I've seen says how to change permissions, not see current ones.

---

### Post by DUKANE on 2010-03-23
You can use
```
ls -l
```

---

### Post by darolu on 2010-03-23
To see permissions and owners:
```
$ ls -l /path/to/your/directory
```
To learn how to change ownership and permissions read this two manuals:
```
$ man chown

$ man chmod
```
For example:
```
$ sudo chown -R user:usergroup /home/user/mydirectory

$ sudo chmod -R ug+x /home/user/mydirectory
```

---

### Post by johngreth on 2010-03-23
Of course. How did I not think of that?

Thanks!

---

### Post by geirha on 2010-03-23
Consider giving [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) a read as well.

---

### Post by johngreth on 2010-03-23
> Consider giving [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) a read as well.

I read that many times in the past, but this time I was just looking to do a specific thing and there was nothing in the table of contents about it. I skimmed the article and didn't see any titles about getting the current permissions. That's what threw me off.

---

### Post by junapp on 2010-03-24
> **johngreth said:**
> Is there a command I can use to get the permissions of a folder in a terminal? Everything I've seen says how to change permissions, not see current ones.
could also use 'stat' and the filename.
```
stat myfile.txt
```

---

