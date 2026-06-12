---
title: "make all users of a certain group own a folder"
date: 2009-10-07
forum: General Help
---

### Post by artheus on 2009-10-07
Is it possible to make all users of a certain group own a folder?

like

```
sudo chown allusers:group /the/folder
```

Thanks!

---

### Post by nothingspecial on 2009-10-07
> **artheus said:**
> Is it possible to make all users of a certain group own a folder?

like

```
sudo chown allusers:group /the/folder
```

Thanks!

As far as I know a file can only have one owner.

If you put all the users in a group and give that group permissions for the file, it accomplishes the same thing.

Please correct me:P

---

### Post by pmlxuser on 2009-10-07
+1 to NothingSpecial ...

---

### Post by artheus on 2009-10-07
Thanks!

How can I give a group permissions to a folder then?

---

### Post by DeBOBAHer on 2009-10-07
In chmod command you give permissions like *ugo* (three digits) - user (owner)/group (owner)/others. So, if you'll change second digit you'll change group permissions.
PS: Or just use mc or other GUI commander for it.

---

### Post by nothingspecial on 2009-10-07
```
chgrp group file
```

Then to give the owner and group full permissions (rwx) but anybody else no permissions
```

chmod 770 file
```

Congratulations, you are the recipient of my 2000th post

---

### Post by callan79 on 2009-10-07
> **nothingspecial said:**
> ```
Then to give the owner and group full permissions (rwx) but anybody else no permissions

+1 for that ... I do exactly the same thing for a folder on my system that I want all family members to use.

My username is callan, and I created a group called 'family'

[code]sudo addgroup family
```

Then I changed the shared folder to be owned by my user, and owned by the family group.

```
sudo chown callan:family /media/shared
```

Then I changed shared's permissions to allow full read/write to family group but nobody else.

```
sudo chmod 770 /media/family
```

Finally added all users to the 'family' group, starting with myself.

```
sudo gpasswd -a callan family
```

So really just the same as nothingspecial said.

Cheers
Callan

---

