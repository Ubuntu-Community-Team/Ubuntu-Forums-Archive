---
title: "member of `admin' but not in sudoers file ?"
date: 2011-06-08
forum: General Help
---

### Post by mme oscar on 2011-06-08
Hi all,

I'm trying to add my single user 'moreaue' to the sudoers. this user seems to be have admin privilege but is not in the sudoers:

```
moreaue@bloom:~$ sudo ls
[sudo] password for moreaue: 
moreaue is not in the sudoers file.  This incident will be reported.
moreaue@bloom:~$ su
Password: 
root@bloom:/home/moreaue# adduser moreaue admin
The user `moreaue' is already a member of `admin'.
root@bloom:/home/moreaue# exit
exit
moreaue@bloom:~$ sudo ls
[sudo] password for moreaue: 
moreaue is not in the sudoers file.  This incident will be reported.
moreaue@bloom:~$ 

```As you can see I can connect as root, run the adduser command which says the user is already admin... but then the user is still not a sudoer.

Of course I can edit the sudoers file manually, but I wonder what is going wrong? Did I miss something?

Thanks!

---

### Post by sisco311 on 2011-06-08
After adding the user to the admin group you have to start a new login shell (log out and log back in).

---

### Post by mme oscar on 2011-06-08
just tried (even restarted the computer):  did'nt work, still not a sudoer. Other ideas?

---

### Post by sisco311 on 2011-06-08
Please post the content of /etc/sudoers

---

### Post by mme oscar on 2011-06-08
/etc/sudoers content:

```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
# %admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
# %sudo    ALL=(ALL:ALL) ALL

#includedir /etc/sudoers.d

```

---

### Post by sisco311 on 2011-06-08
You have to comment out the line **# %admin ALL=(ALL) ALL** (delete the leading # symbol).

Use **visudo** to edit the file.

How did you install ubuntu?

---

### Post by mme oscar on 2011-06-08
ok, it works, thank you!

I did not install it myself on that machine: actually I'm at work, it was installed by a sys admin. Since it's a local machine I asked to have root privilege and they recently accepted, providing me with the root password. I guess this particular configuration was their choice.

Thanks again!

---

### Post by sisco311 on 2011-06-08
> **mme oscar said:**
> ok, it works, thank you!


You're welcome!

> **mme oscar said:**
> 
I did not install it myself on that machine: actually I'm at work, it was installed by a sys admin. Since it's a local machine I asked to have root privilege and they recently accepted, providing me with the root password. I guess this particular configuration was their choice.


I see...

Btw, welcome to the forums!

---

