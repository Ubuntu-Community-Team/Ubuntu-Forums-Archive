---
title: "Missing mysql.user?!"
date: 2006-04-21
forum: General Help
---

### Post by Solan on 2006-04-21
Hi.

I'm trying to get Mediatomb to work, and for that I need MySQL. I'v installed the whole mysql pack, with the server and the holde shabang. The problem is that I can't do anything with the users cuz mysql.user doesn't exist. When I try anything I only get this error message:

## solan@ubuntu:~$ sudo mysqladmin -u root password 12345
## mysqladmin: unable to change password; error: 'Table 'mysql.user' doesn't exist'

What is the matter with it? I'v started the mysql server, and installed mysql-admin. When I try to edit the User Administration in mysql-admin it quits and gives me a strange error:

##  solan@ubuntu:~$ sudo mysql-admin
##
##  (mysql-admin:15250): Gtk-WARNING **: Ignoring the separator setting
##  Segmentation fault
##  solan@ubuntu:~$ sudo mysql-admin

Can any1 help me? Thanks in advance;) 


-Take me drunk, I'm home-

---

### Post by dermotti on 2006-04-21
I've never seen that before.....ide be tempted to say uninstall mysql and reinstall....

---

### Post by Solan on 2006-04-21
Should I uninstall all the mysql components with adept?
I'm not sure if all the installs are there, but I can try;)

Thx for the help;)

-Take me drunk, I'm home-

---

### Post by dermotti on 2006-04-21
Or just use synaptic....

---

### Post by Solan on 2006-04-21
Synaptic?

How do I use that?

-Take me drunk, I'm home-

---

### Post by dermotti on 2006-04-21
Do you have a graphical windows manager installed? Im guessing since you are using Kubuntu you are using KDE.

Anyways synaptic should be in your start menu somewhere, otherwise you can try running **kdesu synaptic** from command line.

If that doesnt work, look for **kpackage**

---

### Post by killerfish on 2006-04-23
Solan,

I'm having the exact same problem.  It just hangs in mysql-admin when I select the User Administration section.. Have you found your solution?

Thanks
KF

---

### Post by Solan on 2006-04-23
Killerfish,

I just reinstalled all the mysql components on my computer, and now it works like a charm:)

-Take me drunk, I'm home-

---

### Post by killerfish on 2006-04-23
Solan,

Do you remember which packages (ie, the names) you had to re-install?

Thanks!
KF

---

