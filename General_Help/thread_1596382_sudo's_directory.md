---
title: "sudo's directory ?"
date: 2010-10-14
forum: General Help
---

### Post by kema_u on 2010-10-14
I use Ubuntu 10.04.1. When i write to terminal "sudo firefox" it opens the firefox with the default users config settings. But when i write "sudo nautilus" it open the nautilus with new config settings. This means there is a problem on my system ? (when i open the firefox with "gksudo", it is using as new user (root user's) config files but nautilus is opening with the root user's files also with "sudo").

---

### Post by lordberic on 2010-10-14
Sudo being the superuser (root) would have it's home directory at /root

if there is not /root directory it will assume that roots home directory is /

that help you? :)

(your system will have a root user even though you can't log on as root from GDM, the user still exists and can be accessed with sudo, also if you wanted to "be" root you can run 'sudo su')

---

### Post by garvinrick4 on 2010-10-14
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by lisati on 2010-10-14
> **lordberic said:**
> Sudo being the superuser (root) would have it's home directory at /root
Yes and no. "sudo" can mean "super user do....". It can also mean "switch user, do". The general effect, however, is still the same: to execute the command as "another" user.

---

### Post by sisco311 on 2010-10-14
> **kema_u said:**
> I use Ubuntu 10.04.1. When i write to terminal "sudo firefox" it opens the firefox with the default users config settings. But when i write "sudo nautilus" it open the nautilus with new config settings. This means there is a problem on my system ? (when i open the firefox with "gksudo", it is using as new user (root user's) config files but nautilus is opening with the root user's files also with "sudo").

My guess is that firefox uses the $HOME environment variable while nautilus reads the location of the user's home directory directly from /etc/passwd.

By default, sudo does not reset $HOME, that's why you should use **sudo -i** or **gksu** for GUI applications.

Oh, and never run your web browser as root.

---

### Post by kema_u on 2010-10-14
(I know that i don't have to open the browser as root but i want to learn how it going on linux)

I know that root user has all permissions and it has a home directory as /root (which has many folders same as /home/myuser)

So when i open firefox or nautilus or any other application, which directory will use this application as home directory to look config files ?

Is the same thing to open the gnome as root or use all applications on gnome as root (i mean with "sudo") ?

---

