---
title: "root password?"
date: 2009-06-27
forum: General Help
---

### Post by ubunt3 on 2009-06-27
During installation I was asked for an id/passowrd but not for a root password. Is there a standard root password? I cannot figure out password for "SU" command. Thanks.

---

### Post by ~sHyLoCk~ on 2009-06-27
> **ubunt3 said:**
> During installation I was asked for an id/passowrd but not for a root password. Is there a standard root password? I cannot figure out password for "SU" command. Thanks.

AFAIK you can't use su in ubuntu, you have to use sudo and your user password to get things done.

---

### Post by sisco311 on 2009-06-27
the root password is locked. 

[uhelp]community/RootSudo[/uhelp]

---

### Post by linuxmagick on 2009-06-27
You should try using sudo instead of su.

Example:  sudo some_command

You will be prompted to type a password.  Just type your regular user password and the command will execute with superuser privileges.  Be sure to replace some_command with the actual command you want to run.

You actually can enable the root account in Ubuntu so you can use su, but I don't see why you'd want to.  With sudo, your privileges are escalated for the duration of a single command.  When you use su, you remain at root until you exit back to your regular user's shell.  It's a security thing,

---

### Post by AoSteve on 2009-06-27
[removed due to rules]

My bad :)

---

### Post by ~sHyLoCk~ on 2009-06-27
> **AoSteve said:**
> You can change the root accounts abilities with the user manager and login manager.  You'd have to enable the "Administrator login" with the login manager and change the password by unlocking the users menu and manually changing it.  

I have already done this and setup my root account as a "basic" account for when I need to do a LOT of "sudo" commands and don't feel like saying "Psuedo" to myself constantly.

I don't think that's a good idea. Running as root can seriously damage your install. Whatever your trying to install or change will have full permission and admin privileges to change whatever it feels like and without asking for your permission. Using root is a threat to the security of your system. But that's just my point of view.

---

### Post by sisco311 on 2009-06-27
> **AoSteve said:**
> ...
please read the [thread=716201]Forum policy on log-in-as-root tutorials[/thread]

---

### Post by AoSteve on 2009-06-27
> **sisco311 said:**
> please read the [thread=716201]Forum policy on log-in-as-root tutorials[/thread]

Thank you for pointing that out, I didn't read that policy as of yet.  I removed my post and will repost with something a bit more towards the "allowed" side.

Sudo is the command you want.

In the terminal it is used for super user permissions...

i.e.   "sudo cp file file2"

This will give super user privileged access to copying file to file2.

A good way to learn about this command is to run this in a maximized terminal window...


```

man sudo

```


I must apologize for giving advice that wasn't with the rules of the forum.  Sorry guys!

---

### Post by linuxmagick on 2009-06-27
> **~sHyLoCk~ said:**
> I don't think that's a good idea. Running as root can seriously damage your install. Whatever your trying to install or change will have full permission and admin privileges to change whatever it feels like and without asking for your permission. Using root is a threat to the security of your system. But that's just my point of view.

I completely agree with your statement.  I used to hate typing sudo because I was so used to using su.  Now one of the first things I do when I install a distro other than Ubuntu is install and setup sudo.  Now I don't know how I ever lived without it.:)

---

