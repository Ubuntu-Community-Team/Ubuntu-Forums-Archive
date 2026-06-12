---
title: "change super user?"
date: 2010-06-04
forum: General Help
---

### Post by jomex on 2010-06-04
how do i create a new super user account and degrade my initial account to a normal user?

i just created a new user "myadmin" in "users and groups" and set the type to "administrator" and my initial user account to "desktop user"... with the result that X isn't working anymore and when i try to "sudo ..." with my desktop user, i'm prompted for the users password but the command fails because user is not a su.

---

### Post by lisati on 2010-06-04
Before we begin, have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jomex on 2010-06-04
```

root    ALL=(ALL) ALL
%sudo ALL=(ALL) ALL
%admin ALL=(ALL) ALL

```i think it reads: everyone in sudo or admin group is a sudoer

however, when i do "sudo echo bla" as user i'm prompted for the user password not the su password? i expected to enter the "myadmin" password.

---

### Post by bodhi.zazen on 2010-06-04
After you done with that link ...

You can keep one administrative account , the use is in the admin group.

Make a new user who is not in the administrative account.

BUT ...

Linux is not windows. Administrative accounts **are restricted** accounts with the privilege of escalating to "the" administrative account (root) which requires your log in password.

Regular accounts can not access root at all.

Try making a change to ext/fstab from your account, without accessing root via sudo

```
gedit /etc/fstab
```

You can read the file , and edit it, but you can not save your changes.

---

### Post by bodhi.zazen on 2010-06-04
> **jomex said:**
> ```

root    ALL=(ALL) ALL
%sudo ALL=(ALL) ALL
%admin ALL=(ALL) ALL

```i think it reads: everyone in sudo or admin group is a sudoer

however, when i do "sudo echo bla" as user i'm prompted for the user password not the su password? i expected to enter the "myadmin" password.

That is how sudo works, the user password is used. You can change the behavior if you wish , see man sudoers

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

---

### Post by jomex on 2010-06-04
> Regular accounts can not access root at all.

so there is no way to "sudo" with a desktop user?

---

### Post by jomex on 2010-06-04
okay, what i need is when i type: sudo foo
i want to actually use the "myadmin" account and also be prompted for the admin account

---

### Post by bab1 on 2010-06-04
There is only one superuser (root).  The term ***su ***means "switch user".  You can switch to other users too.  As in ```
su bill
``` with the proper pass you will run as the user *bill*.

---

