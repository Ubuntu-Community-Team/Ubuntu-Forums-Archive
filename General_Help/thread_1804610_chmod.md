---
title: "chmod"
date: 2011-07-14
forum: General Help
---

### Post by YK3bug on 2011-07-14
How can I change the permissions of a directory, along with everything in it with chmod?
I want the permissions changed to:

Owner: Create and delete files
Group: Access files
Others: Access files

---

### Post by bodhi.zazen on 2011-07-15
> **YK3bug said:**
> How can I change the permissions of a directory, along with everything in it with chmod?
I want the permissions changed to:

Owner: Create and delete files
Group: Access files
Others: Access files

Permissions of directories are not the same as permissions for files.

For directories you will want permissions of 755
For files you will want permissions of 644

See :  [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by 3rdalbum on 2011-07-15
Have you had a look at the chmod man page:

```
man chmod
```

There's several different ways of using chmod - the easiest for you to understand would be something like this:

```
sudo chmod o+rw <folder>
sudo chmod g+r <folder>
sudo chmod a+r <folder>
```

but I'm sure there are more efficient ways of doing it.

---

### Post by bodhi.zazen on 2011-07-15
> **3rdalbum said:**
> Have you had a look at the chmod man page:

```
man chmod
```There's several different ways of using chmod - the easiest for you to understand would be something like this:

```
sudo chmod o+rw <folder>
sudo chmod g+r <folder>
sudo chmod a+r <folder>
```but I'm sure there are more efficient ways of doing it.

You need +x on directories ;)

---

