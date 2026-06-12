---
title: "Renaming a Username and Computer name"
date: 2011-11-23
forum: General Help
---

### Post by Kruger2147 on 2011-11-23
I'm putting together a computer at work, while setting it up I accidentally go the Username and Computer name mixed up. I don't really want to have to go through and reformat and install Ubuntu. How to I rename a User and the computer via the terminal?

---

### Post by quadproc on 2011-11-23
If I understand your situation correctly, the fix should be simple.

First, the computer name is in the file /etc/hostname.  Use your favorite editor to change the name.  You will need to be privileged to save the edited file.

To change the user name, add a new user of the desired name to your list of users.  Give the new user appropriate privilege.  Of course, you will need to be privileged to do this.  When the new user is satisfactorily installed, delete the old, incorrect user.

quadproc

---

### Post by Kruger2147 on 2011-11-23
Yea, I'm still a nub. I'm just following directions that a coworker printed out and gave to me. How do I do that? Where do I go?

---

### Post by oldtimer7777 on 2011-11-23
> **Kruger2147 said:**
> Yea, I'm still a nub. I'm just following directions that a coworker printed out and gave to me. How do I do that? Where do I go?

Just create a new user named what you need it to be named, either in Users and Groups or in User Account settings.  

To rename your computer:

[http://www.brighthub.com/computing/linux/articles/12306.aspx](http://www.brighthub.com/computing/linux/articles/12306.aspx)

---

### Post by fdrake on 2011-11-23
to chnge user login name
```

sudo su
usermod -l new_name old_name

```
Note: login first using another user (or login directly to root). You cannot change a user who is already logged in!

to change hostname (+1 @quadproc)
```
sudo gedit /etc/hostname
sudo gedit /etc/hosts

```
also suggest to to edit you DNS hosts file , the line that has your old hostname

---

