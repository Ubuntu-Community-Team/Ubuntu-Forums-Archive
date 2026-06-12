---
title: "Best option for sharing files locally"
date: 2009-08-12
forum: General Help
---

### Post by ricardisimo on 2009-08-12
[LIST=1]
[*]Create a separate partition on the hard disk, and have everyone's Home folders have a symlink to it;
[*]Create a folder somewhere below / but above individual Home folders with no permission restrictions.
[/LIST]
This would include all of our music and photos, so that my wife doesn't need a password to see them, nor do any of her apps fail when accessing them. Thanks.

---

### Post by regala on 2009-08-12
> **ricardisimo said:**
> [LIST=1]
[*]Create a separate partition on the hard disk, and have everyone's Home folders have a symlink to it;
[*]Create a folder somewhere below / but above individual Home folders with no permission restrictions.
[/LIST]
This would include all of our music and photos, so that my wife doesn't need a password to see them, nor do any of her apps fail when accessing them. Thanks.

to be able to access some files or directories, one only needs permissions to do so. no need to have a partition, or symlink. The real issue is done by creating a group (e.g. "share")
```
groupadd share
```
then put every user you want in that group
```

adduser luser share
adduser darling share

```

then, you need any file to be fully accessed to be set 664, and any directory you want the members of share to be able to write or unlink into, to be set 775.

```

chmod 664 file
chmod 775 directory

```

the question of where you put these files is second to the problem of access rights.

br, mathieu

---

### Post by ricardisimo on 2009-08-12
So, there aren't any apps out there that will automatically take issue with accessing a folder outside of "Home"?

---

### Post by regala on 2009-08-13
> **ricardisimo said:**
> So, there aren't any apps out there that will automatically take issue with accessing a folder outside of "Home"?

no, if the user exec'ing the apps can access that folder... I'm not sure I understood the question.

In fact, in Unix systems, the filesystem(s) is (are) organized as a tree, starting with /.
First, there are only few rules to access a file (file here means file or directory)

- to be able to read the content of the file, you must have READ access
- to be able to write the content of the file, you must have WRITE access (not necessarily READ access)
- a directory is a "special" file that you need the READ and EXEC right to access into
- a file in a directory is only kind of an entry in a text file (that would be the directory), so to **create** or **delete** a file, you do not need the READ/WRITE access to the file (in the case of deleting the file), BUT the WRITE access to the upper directory

In GNU/Linux systems, you usually access any folder you want, except a few ones where it would be serious security-hazard for anyone to see :)
So don't worry about accessing your filesystem mostly, and don't forget that "Home" is, usually, nothing but /home/login, a folder amongst many others on your box.

br, mathieu

---

### Post by asmoore82 on 2009-08-13
```
sudo mkdir /home/Shared
sudo chown 0:users /home/Shared
sudo chmod 1775 /home/Shared
```
^That last line sets the permissions on the shared folder as "sticky" -
so that users can cannot delete each other's read-only files.

---

### Post by ricardisimo on 2009-08-13
Fantastic. Thank you all very much.

---

