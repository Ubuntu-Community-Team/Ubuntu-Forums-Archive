---
title: "gedit terminal error after sudo su"
date: 2006-04-04
forum: General Help
---

### Post by dalyraptor on 2006-04-04
i get the following error message in the terminal, after which typing commands will not work so i have to open another terminal, which is annoying. is there any shortcut for opening the terminal or how do you add a shortcut?

michael@ubuntu:~$ sudo su
root@ubuntu:/home/michael# gedit

(gedit:9051): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by dcstar on 2006-04-04
[QUOTE=dalyraptor]i get the following error message in the terminal, after which typing commands will not work so i have to open another terminal, which is annoying. is there any shortcut for opening the terminal or how do you add a shortcut?

michael@ubuntu:~$ sudo su
root@ubuntu:/home/michael# gedit

(gedit:9051): GnomeUI-**WARNING** **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/QUOTE]
That is a Warning message, it is not an error.

If you exit gedit, you will be dropped back to a prompt, which is exactly how it is supposed to work.

Gedit is a graphical app, it is meant to be started from a launcher, you can start it from a terminal and you will get messages like that which don't affect the application one iota.

If you want to launch terminal sessions, you create a launcher with "gnome-terminal" as the command - or right-click vacant desktop space and select the appropriate option.

---

