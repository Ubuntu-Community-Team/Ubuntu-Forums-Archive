---
title: "change file permissions"
date: 2009-12-22
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2009-12-22
is there a command to set all files and folders including sub files and sub folders permissions to the normal user
lets say that /home/user/ has a lot files that require root access all over the place
not something i want to do for every sub folder if you know what i mean

---

### Post by doas777 on 2009-12-22
ok, are you sure we are talking about /home/<user> ?
if not, changes could render your system unbootable or otherwise broken.

the command you probably want is 
```

sudo chown -R <user>:<usergroup> <path>
sudo chmod -R u+rw <path>

```

just be sure to specify the path correctly.

---

### Post by anaconda on 2009-12-22
Dont change the permissions of EVERY file in your home folder!!

That would propably prevent you from logging in!!

I think there are atleast 2 hidden files which have to have the rights they have.
Was one of them .dmrc  ?? Dont remember, but I once changed the permissions of every file in my home directory, and after that I had some problems..

---

### Post by pqwoerituytrueiwoq on 2009-12-22
> **anaconda said:**
> Dont change the permissions of EVERY file in your home folder!!

That would propably prevent you from logging in!!

I think there are atleast 2 hidden files which have to have the rights they have.
Was one of them .dmrc  ?? Dont remember, but I once changed the permissions of every file in my home directory, and after that I had some problems..
undoing that is what i trying to take care of
/media/disk/home/user/* 
needs root permissions

---

### Post by doas777 on 2009-12-22
> **anaconda said:**
> Dont change the permissions of EVERY file in your home folder!!

That would propably prevent you from logging in!!

I think there are atleast 2 hidden files which have to have the rights they have.
Was one of them .dmrc  ?? Dont remember, but I once changed the permissions of every file in my home directory, and after that I had some problems..

the trick with .dmrc is that the file must be owned by the user, and writable by noone except the user. so you could have perm of 600 while owned by user:somegroup, or 
660 when owned by user:user. I believe the default permissions are 640 user:user.

---

