---
title: "permission problem"
date: 2006-05-14
forum: General Help
---

### Post by learning curve on 2006-05-14
I need to empty my trash.  I keep getting an error that I don't have permission to empty because i don't own  the parent directory home.  It is owned by root and I don't no how to change it.  Any ideas?

---

### Post by thunderduck3141 on 2006-05-14
well
you could log in as root
or type
sudo cd (whatever trash is under)
then erase all the files through the command line
or you could change the permissions of your user by going to System>Admistration>UsersandGroups

---

### Post by learning curve on 2006-05-14
How do I log in as root?

---

### Post by aysiu on 2006-05-14
You don't own the parent directory, home? Well, it's true--you don't.

You own /home/username.

But, the trash usually lives within /home/username. In Gnome, it lives in /home/username/.Trash, so you should own the parent directory.

It is possible that a non-user-owned file may have ended up in your trash. If that's the case, paste this command into the terminal: ```
sudo rm -rf ~/.Trash/*
``` You may also want to run ```
sudo chown -R *username*:*username* /home/*username*
``` Substitute *username* with your own real username, of course.

---

### Post by aysiu on 2006-05-14
[QUOTE=learning curve]How do I log in as root?[/QUOTE] You never need to log in as root:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by learning curve on 2006-05-14
Thanks Aysiu.  All worked great.

---

