---
title: "Simple permissions question"
date: 2010-01-31
forum: General Help
---

### Post by deekthesqueak on 2010-01-31
I can't seem to figure out this permissions question.

I have a user lets call it mainuser1 with a home directory /home/mainuser1.  In that folder I have another folder called beta.  I want another user (extrauser2) to be able to have read-only access that folder not anything above it.  I created a group called foldershare which extrauser2 is member of.  The permissions of the folders is as follows:

/home/mainuser1 : ```
drwxr-x---  4 mainuser1   mainuser1  4096 Jan 31 18:57 mainuser1
```
/home/mainuser1/beta : ```
drwxr-----  3 mainuser1 foldershare      4096 Jan 31 18:57 beta

```

Why can't extrauser2 access /home/mainuser1/beta?

---

### Post by raktarok on 2010-01-31
Maybe because the folder mainuser1 does not have read access for other users/groups except mainuser1?

Make the permissions of the mainuser1 folder something like this: drwxr-xr--
It should work now.

---

### Post by deekthesqueak on 2010-02-01
If I did that wouldn't all users be able to have read access to /home/mainuser1?  Can't I set read permissions for the subfolder beta (/home/mainuser1/beta) and not allow read access to /home/mainuser1?

---

### Post by t4thfavor on 2010-02-01
Don't you need r-x to actually read the files and cd into the dir? I don't think other permissions are nessecary though. Just keep experimenting, and you will get it. There are only so many combinations.


If you have nautilus installed you can use it to manage permissions with varying levels of success.

---

### Post by deekthesqueak on 2010-02-01
This is on a server so I have command line only.  I have sudo on a user so I can switch to a user to check permissions.

Changed permissions on /home/mainuser1/beta to 750 (drwxr-x---) then did sudo su extrauser2 to check if I can get into the folder.

cd /home/mainuser1/beta gives me:
```
bash: cd /home/mainuser1/beta: Permission denied
```

What it looks like is that even though /home/mainuser1/beta has the permissions I want, the fact that /home/mainuser1 has ```
drwxr-x---  4 mainuser1   mainuser1  4096 Jan 31 18:57 mainuser1

``` is blocking access because if I change the group on /home/mainsuer1 to foldershare I have access to /home/mainuser1/beta but also everything in /home/mainuser1 which I don't want to happen.

---

### Post by t4thfavor on 2010-02-01
I will have to defer to somebody who is more in tune with the file system permissions than I am. Sorry.

Like this guy

[http://www.33dots.com/index.php/linux/revisiting-file-access-modes-in-linux.html](http://www.33dots.com/index.php/linux/revisiting-file-access-modes-in-linux.html)

You have to have x for everyone on the parent directory, or you cannot cd into the subdirectory.

I have tested the above method, and confirmed that we CAN cd into the home dir, we cannot ls or do anything else at all.

---

### Post by deekthesqueak on 2010-02-01
That would be the problem! :) Thanks for the help.

---

### Post by t4thfavor on 2010-02-01
Mark this solved with the thread tools then, Glad you got it handled. 

I think the first post back had the right idea, he just didn't explain it to us simple folk well enough.

---

