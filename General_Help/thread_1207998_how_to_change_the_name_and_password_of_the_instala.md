---
title: "how to change the name and password of the instalation user?"
date: 2009-07-08
forum: General Help
---

### Post by reignaldo on 2009-07-08
how to change the name and password of the instalation user?

---

### Post by Jebtrix on 2009-07-08
In terminal:

This will change currently logged in user's pwd.
```
passwd
```


These will change username and profile folder name (use at own risk)
```
usermod -l newname oldname
usermod -u UID newname
```

---

### Post by reignaldo on 2009-07-10
error:
UserMode: unable to get lock on file passwords

---

### Post by credobyte on 2009-07-10
> **reignaldo said:**
> error:
UserMode: unable to get lock on file passwords

```
**sudo** your_command

```

---

### Post by reignaldo on 2009-07-10
[SIZE=5]error:
usermod : argumento numérico `UID' inválido
[/SIZE][SIZE=5]numeric argument UID invalid
but the name has changed. ok.
now, can I change the password created at the installation? is different of the user password.
[/SIZE]

---

### Post by rabdoel on 2009-07-10
and if command line is a bit to much then

from the gnome menu select system>administration>users and groups . . hit properties on the user you need to change password for and change password.

---

### Post by reignaldo on 2009-07-10
[SIZE=4][rabdoel]("http://ubuntuforums.org/member.php?u=871974"), there is user password, how to change the system password? created on the installation ?
The user "root" is disabled to change password.
[/SIZE]

---

### Post by rabdoel on 2010-01-09
ok so its been a long time I have been here , but am now back 

if you are still looking for the answer..

define system password ? what do you mean with system password ?
system password as the root password ?
or system password of the user ?

I think you are looking for the root password, so when you open up the users and groups
you can change the users password , which will be your normal user name , or you can change the root password . I think you want the root password.. select root account and then select properties .

in the box "set password by hand "
for user password . make a password and confirm the password .. done your root password is changed now. every-time you will do something that requires admin privileges you will be asked for this password.

and the root is not disabled .. you need to click the icon at the bottom that says "click to make changes " put in your current root password and then the root account can be changed .

sorry if this answer is to late , I am sure you have managed to solve this already

---

### Post by Elfy on 2010-01-09
Closed - OP has not been here since July 2009.

---

