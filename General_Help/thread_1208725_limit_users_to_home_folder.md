---
title: "limit users to home folder"
date: 2009-07-09
forum: General Help
---

### Post by theraininspain on 2009-07-09
I need to limit users to only access their home folder.
I tried chmod and ended up fubaring their account (till i chmod'd it back).

I'm relatively new to linux.

---

### Post by bostonaholic on 2009-07-09
> **theraininspain said:**
> I need to limit users to only access their home folder.
I tried chmod and ended up fubaring their account (till i chmod'd it back).

I'm relatively new to linux.

unless they have the root password, by defualt users only have access to /home/<username> (and subfolders created by that user)

---

### Post by theraininspain on 2009-07-09
> **bostonaholic said:**
> unless they have the root password, by defualt users only have access to /home/<username> (and subfolders created by that user)

no, i tried to make sure. they have access.

Is there a chmod so i can specifically remove access for just one group?

---

### Post by DeMus on 2009-07-09
> **theraininspain said:**
> no, i tried to make sure. they have access.

Access to what?

---

### Post by asmoore82 on 2009-07-09
they have to be able to read and execute most of the system files to use the computer ...

Do you mean you want to make sure they can't read each other's files?
You can make all of the home directories private like this:
```
sudo chmod 700 /home/*
```

---

### Post by bostonaholic on 2009-07-09
> **asmoore82 said:**
> they have to be able to read and execute most of the system files to use the computer ...

Do you mean you want to make sure they can't read each other's files?
You can make all of the home directories private like this:
```
sudo chmod 700 /home/*
```

I didn't think of it like that.  I thought OP meant system files.

Yes, think of the file permission as user:group:other

```
chmod 700 /home/<username>
``` will give read/write/execute permssions to the owner, and no permission to the group and other users.

Like asmoore82 said, I think 700 is what you're looking for here.

---

### Post by theraininspain on 2009-07-09
> **bostonaholic said:**
> I didn't think of it like that.  I thought OP meant system files.

Yes, think of the file permission as user:group:other

```
chmod 700 /home/<username>
``` will give read/write/execute permssions to the owner, and no permission to the group and other users.

Like asmoore82 said, I think 700 is what you're looking for here.

they can still access /

---

### Post by bostonaholic on 2009-07-09
> **theraininspain said:**
> they can still access /

I just did a ```
sudo chmod 700 /var
``` and it won't allow me to cd into /var.

You haven't really explained what you want each user to access and what each user cannot access.  Once we know that, we can get you the correct file permissions.

---

### Post by michy99 on 2009-07-09
If they can't access anything outside their home folder, how can they run any programs?

---

### Post by twright on 2009-07-09
Users need to be able to have read access to files outside of their home folders for them to be able to do anything. The default permission are secure, if you want to make it more so then I suggest you detail exactly what you want to do and why and people might be able to give more relevent advice.

---

### Post by statistic on 2009-07-09
Perhaps little more detail for you to see why users need to be able to read and execute outside their home folders:

All the main commands in the system rest in folders like /usr/bin, so in order to use any commands, they need read and execute to all those binaries, and the folder itself, and subsequently it's parent folders (/usr in this case). Even the command line shell they are presented with at login is a binary residing elsewhere in the system that their user needs to be able to read/execute.

A properly configured system, which is how a fresh installation will come, will have permissions that users really shouldn't be able to read already has no read permissions, and every other file on the system (with the exception of /tmp) will not allow them to write outside their home folder. Really the only thing you'll need to worry about is a user poking through another user's home folder. So a simple "chmod 700 /home/*" should clean that problem right up. Or use 701 in case you want a webserver to be able to read public_html files and the like.

---

### Post by ajgreeny on 2009-07-10
> **theraininspain said:**
> they can still access /
Yes, they can still access it but they can't do anything to it unless they have the admin password, ie, if they are not in the admin group they can look at (read) but not edit or change or delete anything.

---

