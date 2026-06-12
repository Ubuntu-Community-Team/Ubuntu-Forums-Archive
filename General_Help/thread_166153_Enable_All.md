---
title: "Enable All"
date: 2006-04-25
forum: General Help
---

### Post by Sonic5688 on 2006-04-25
How do I give myself total access to do anything I want in Ubuntu? Like making myself an owner or giving myself root access or something like that?

---

### Post by enopepsoo on 2006-04-25
[QUOTE=Sonic5688]How do I give myself total access to do anything I want in Ubuntu? Like making myself an owner or giving myself root access or something like that?[/QUOTE]

It is not recommended, but you can log in using the root account.  [Automatix]("http://www.ubuntuforums.org/showthread.php?t=138405") sets up a root account by defult I believe.  Perhaps by using automatix you can avoid running as root by using the root scripts (gedit and nautilus "here" on right click) to work around not being able to delete things in /bin :p 

The Ubuntu way of doing things is just sudo command at the terminal.

---

### Post by white_tiger_daniel on 2006-04-25
Well you really shouldn't want to be root because if you make errors you can stuff up pretty bad.  You can go to (I think) Administration > Users and Groups > (your user) > Edit (I think) and somewhere you should see a place where you can edit your privelleges. If you want root acess in a terminal type 'sudo' before your commands.

---

### Post by cracker on 2006-04-26
Also, for a root terminal session, enter sudo -i, and it will ask you for your password, then you will have root access until you close it or exit.

---

### Post by xhie on 2006-04-26
Well by defualt ubuntu gives the first user account created sudo privledges. Meaning you can use sudo for anything you want to do, which is the equivalent of being root for all purposes.

---

