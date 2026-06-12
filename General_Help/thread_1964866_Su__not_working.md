---
title: "Su  not working"
date: 2012-04-24
forum: General Help
---

### Post by codingman on 2012-04-24
I'm testing Ubuntu 12.04, and waiting for a launchpad account, but I thought I would try here first. When I type in terminal "su" it asks for my password to become superuser, but when I enter my password, it says authentication failed. Whereas when I do sudo for an application, it works!:mad::mad:

---

### Post by jonobr on 2012-04-24
try
```
sudo su 
```
instead

---

### Post by strask on 2012-04-24
sudo and su do not do the same thing.

sudo runs a command as root. It asks for the current user's password.

su switches user to root. It asks for root's password. On most modern linux systems, root does not have a password set so this will fail.

The recommended way to get a root shell is with ```
sudo -i bash
```

---

### Post by sisco311 on 2012-04-24
su promts for the targed user's password, by default root. But the root account password is locked in Ubuntu. See: [uhelp]community/RootSudo[/uhelp].

And please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by sisco311 on 2012-04-24
@ strask and jonobr

The recommended way to start a root shell is:
```
sudo -i
```

---

### Post by strask on 2012-04-24
> **sisco311 said:**
> @ strask and jonobr

The recommended way to start a root shell is:
```
sudo -i
```
Hi sisco311. Was my way wrong, or just too verbose?

---

### Post by Cheesemill on 2012-04-24
> **strask said:**
> Hi sisco311. Was my way wrong, or just too verbose?
Your method opens a different shell than Ubuntu's default.
Ubuntu uses Dash, not Bash as it's shell.

---

### Post by sisco311 on 2012-04-24
> **strask said:**
> Hi sisco311. Was my way wrong, or just too verbose?

Neither, but the recommended way is **sudo -i**. :) 

**sudo -i** simulates an initial login. It runs the shell specified by the password database entry (/etc/passwd) of the target user as a **login shell**.

While **sudo -i bash** will start an interactive non-login bash shell.  


For the differences between a login and non-login bash shell, please check out:
```
man bash | less '+/^INVOCATION'
```

---

### Post by strask on 2012-04-24
> **Cheesemill said:**
> Your method opens a different shell than Ubuntu's default.
Ubuntu uses Dash, not Bash as it's shell.

Oh my. Thanks for pointing this out... I've been away from linux for a long time and just installed 11.10 a couple days ago, hadn't noticed this. :oops:

Edit: And thanks again sisco for your info too.

---

### Post by sisco311 on 2012-04-24
> **Cheesemill said:**
> Your method opens a different shell than Ubuntu's default.
Ubuntu uses Dash, not Bash as it's shell.

Nope. The default system shell (used by the init scripts etc.) is dash, but the default user shell is bash.

---

### Post by jonobr on 2012-04-24
Learned a lot from this thread 

thanks all

---

### Post by codingman on 2012-04-27
Hee hee, I messed up F16 from Ubuntu, thanks, both sudo -i and sudo su work. Thanks for everyone's input!

---

