---
title: "Unable to unpack to folder"
date: 2009-10-25
forum: General Help
---

### Post by m0sh on 2009-10-25
Hey.. im trying to install a screen saver to my system.  In the readme it says to unpack to the following location:

> /usr/share/gnome-screensaver/Its giving me me an error saying I don't have permission to do so.  How can I move the files to that location?  Any suggestions would be highly appreciated.  Thanks guys.

---

### Post by Jarr0d on 2009-10-25
Use sudo to do the copy?

The directory is locked down for writing access.

root@desktop:/usr/share# ls -al | grep gnome-screensaver
drwxr-xr-x    2 root root  4096 2009-04-21 00:03 gnome-screensaver

---

### Post by m0sh on 2009-10-25
I tried entering
> root@desktop:/usr/share# ls -al | grep gnome-screensaver
into the terminal but it gave me an error saying
> bash: root@desktop:/usr/share#: No such file or directory

Sorry I'm really new to Ubuntu. Thanks for the reply by the way.

---

### Post by martrn on 2009-10-25
Type :
```
sudo chmod 666 /usr/share/gnome-screensaver/     # or
sudo chmod 777 /usr/share/gnome-screensaver/     # if executables there
```
first then that will modify the permissions of the dirctory to make the permissions read/writable.

Try 
man chmod
to learn about the chmod command.

---

### Post by Jarr0d on 2009-10-25
Sorry that was me showing the listing of files in the folder.

For the unpack command in the readme, put 

*sudo*

infront of it.

---

### Post by m0sh on 2009-10-25
Awesome.. worked perfect! Thanks a lot I really appreciate it.

---

