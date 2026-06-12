---
title: "Sym Link as Home Folder"
date: 2009-10-14
forum: General Help
---

### Post by zzzBrett on 2009-10-14
I have a file server (among other services) that has various users with samba shares as /media/HDD/username.  Each user also has a home folder, /home/username.  I would like the home folder and the user's /media/HDD folder to be the same.

Would anything 'break' if I simply moved the contents from the home folders to the /media/HDD/* folders, then deleted the home directories and created a symlink for each user?

---

### Post by PeEllAvaj on 2009-10-14
I'm not certain about moving individual home folders, but my /home/ folder is a sym link to /super/homes/ which is on my RAID array, meaning you can sym link /home/ to another drive, or another computer.

---

### Post by karlson on 2009-10-14
> **zzzBrett said:**
> I have a file server (among other services) that has various users with samba shares as /media/HDD/username.  Each user also has a home folder, /home/username.  I would like the home folder and the user's /media/HDD folder to be the same.

Would anything 'break' if I simply moved the contents from the home folders to the /media/HDD/* folders, then deleted the home directories and created a symlink for each user?

No.  But I would make /home a link to /media/HDD instead or just set users' home to /media/HDD/<user> instead of creating links.

You can also make /media/HDD default home directory for user creation if you want to.

---

### Post by zzzBrett on 2009-10-14
> **karlson said:**
> **No.  But I would make /home a link to /media/HDD instead or just set users' home to /media/HDD/<user> instead of creating links.**

You can also make /media/HDD default home directory for user creation if you want to.

That is perfect.. thanks.  idk why I didn't think of that :)

---

### Post by bodhi.zazen on 2009-10-14
> **karlson said:**
> No.  But I would make /home a link to /media/HDD instead or just set users' home to /media/HDD/<user> instead of creating links.

You can also make /media/HDD default home directory for user creation if you want to.

Or use bind

mount --bind /media/HDD /home

you can put a line in fstab if you wish

You can also specify a home directory

usermod -d /media/HDD/user_name -m

> 
**-d**, **--home** *HOME_DIR* The user's new login directory. If the **-m** option is given the contents of the current home directory will be moved to the new home directory, which is created if it does not already exist.[http://linux.die.net/man/8/usermod](http://linux.die.net/man/8/usermod)

---

### Post by zzzBrett on 2009-10-14
> **bodhi.zazen said:**
> Or use bind

mount --bind /media/HDD /home

you can put a line in fstab if you wish

You can also specify a home directory

usermod -d /media/HDD/user_name -m

[http://linux.die.net/man/8/usermod](http://linux.die.net/man/8/usermod)

Is there any advantage of bind over symlinks?

---

### Post by bodhi.zazen on 2009-10-14
The major advantage, if you have a number of users, it is a "one liner" rather then having to make a symlink for each user.

If you symlink /home it would not matter.

--bind will be "invisible" to your users (for the most part).

---

