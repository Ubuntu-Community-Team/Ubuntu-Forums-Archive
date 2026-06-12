---
title: "Permissions issues chown command?"
date: 2011-07-03
forum: General Help
---

### Post by hakermania on 2011-07-03
If I have 4 users in the PC and I want two of them to have permissions of a folder recursively, how is the command to do it? (assuming that now the files belong to root and only)

I have tried:
```

root@PC:/home# chown user1:user1 user2:user2 -R foldername

```
But it doesn't work
```

chown: cannot access `user2:user2': No such file or directory

```

Thanks in advance for any answers!

---

### Post by andrewthomas on 2011-07-03
> **hakermania said:**
> If I have 4 users in the PC and I want two of them to have permissions of a folder recursively, how is the command to do it? (assuming that now the files belong to root and only)

I have tried:
```

root@PC:/home# chown user1:user1 user2:user2 -R foldername

```
But it doesn't work
```

chown: cannot access `user2:user2': No such file or directory

```

Thanks in advance for any answers!

A file or folder can only have one owner, you are trying to assign two.

What you can do is make one of the users the owner and make a group that contains both users the group owner.

Then you can 

```
chmod -R 664 /path/to/folder
```

---

### Post by Morbius1 on 2011-07-03
I can't quite follow this either but if you issue a:
```
chmod -R 664 /path/to/folder
```You won't be abe to open the folder. Folders need the execute bit to be turned on. So I would suggest the following:
```
chmod -R a+rwX,o-w /path/to/folder
```The big "X" will make every folder executable and leave all files not executable except those that are already executable.

EDIT: There's no way to achieve this with an octal chmod.

---

### Post by hakermania on 2011-07-04
Thanks, what I finally did was to add the user I wanted(www-data) to an existing group(alex)
```

usermod -a -G alex www-data

```
where group 'alex' contained the other user as well
and then
```

sudo chown -R alex /var/www

```
and it worked...!

---

