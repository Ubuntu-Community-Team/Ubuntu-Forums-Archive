---
title: "I cant access su."
date: 2009-10-20
forum: General Help
---

### Post by Onforty on 2009-10-20
Hey guys, having a trouble with installing Nethack, i need to go su..
But where can i get the password, it didnt ask to change it at installation, nor at an time while operated.

So, there must be a default password wich i dont know.
Its my computer, not the Ubuntu Dev Team, give me help as fast as you can.

---

### Post by sahabcse on 2009-10-20
Type in terminal

#sudo passwd

it will ask to enter your system user password then enter your super user new password also confirmation.

---

### Post by Neezer on 2009-10-20
> **Onforty said:**
> Hey guys, having a trouble with installing Nethack, i need to go su..
But where can i get the password, it didnt ask to change it at installation, nor at an time while operated.

So, there must be a default password wich i dont know.
Its my computer, not the Ubuntu Dev Team, give me help as fast as you can.

when you start ubuntu for the first time, the user created also has admin rights. when using sudo as this user, just use the password that you put in the first time you started up.

---

### Post by petersohn on 2009-10-20
Ubuntu has a policy that it's better not to have a root password, and instead use your admin account and sudo. If you need a root shell, just type "sudo su -".

---

### Post by snova on 2009-10-20
> **Onforty said:**
> Hey guys, having a trouble with installing Nethack, i need to go su..

If you're installing from source (it sounds like it), you don't have to. Use Synaptic and search for "nethack", I think the package is nethack-x11 (or nethack-qt for an alternate, Qt-based interface, or nethack-console for terminal mode).

> But where can i get the password, it didnt ask to change it at installation, nor at an time while operated.

So, there must be a default password wich i dont know.
Its my computer, not the Ubuntu Dev Team, give me help as fast as you can.

[There is no root password...]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Onforty on 2009-10-21
Oh sorry for bugging about with the root password.. I am still a retarded Windows user, -"First cup of Ubuntu" as you guys say.

[SIZE=7]But it worked thanks :)[SIZE=1]

Seriously thanks :)
[/SIZE][/SIZE]

---

### Post by akakingess on 2009-10-21
No problem, you will find most of the people on here very helpful and friendly, so just stick with it and before long you won't even remember the name of that other OS.

---

