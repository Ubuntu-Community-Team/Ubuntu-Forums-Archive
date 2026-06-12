---
title: "Defualt permissions"
date: 2011-07-18
forum: General Help
---

### Post by hojjat on 2011-07-18
Let's say we have two users in a group. Each of them store some files in their home directory. There is also a common directory (let's call it /project) that they both use to share some stuff with each other.

I want the default permission for files and directories they create in the /project to be 771, letting the other user of the group to have full control on the files.

However, the default permission for files and directories they create in their home directory should be 710, only letting other users of the same group to read, and preventing outsiders to even access the files.

What configurations should I use (both for the user's profiles and for the /project permission) to make this possible? They are both using bash for terminal.

---

### Post by CharlesA on 2011-07-18
The other user isn't part of the original users group so permissions of 775 would be fine.

---

### Post by hojjat on 2011-07-18
I thought I was clear enough, but just in case: I want the default permission of all files and directories they create to be as I explained (i.e. it should depend on the directory in which they create things).

---

### Post by CharlesA on 2011-07-19
The permissions will still be wrong, read access isn't "1" for chmod:

4 - Read
2 - Write
1 - Execute

How are you accessing that directory? You could change the umask, but that is a global setting.

---

### Post by hojjat on 2011-07-21
I know. That was a typo. My question is not about using chmod, my question is about how can I enforce different default permissions in different directories?

---

### Post by Morbius1 on 2011-07-21
Having 77x isn't enough since each time user1 saves a file it will be 
owner = user1
group = user1

You need to add a setgid bit on the shared directory ( which will force all new files to inherit the group of the parent folder ):
```
sudo chmod 2770 /project
```Set the group of the shared directory to your special group
```
sudo chown :special-group /projects
```And then change the global umask as suggested above by editing /etc/profile and changing the last line from "umask 022" to:
```
umask 002
```Now when user1 adds a file it will save as:
owner = user1
group = special-group
Files will have 664 permissions
Folders will have 775 permissions

**[COLOR=Blue]EDIT[/COLOR]:** The setgid bit allows every user to delete the other users files. To prevent that from happening you might want to change the chmod command to this:
```
 sudo chmod 3770 /project
```The "3" is the setgid bit (2) + the sticky bit ( +1) which will allow only the original user and root to delete the file.
[B]
[COLOR=Blue]EDIT2[/COLOR]:[/B] Sorry about all these edits. "profile" is only read once at login so if you change umask you need to logout and login again.

---

