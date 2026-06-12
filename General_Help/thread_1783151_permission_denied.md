---
title: "permission denied"
date: 2011-06-15
forum: General Help
---

### Post by crazylinux on 2011-06-15
Hi,
I want to edit /etc/X11/xorg.conf file in ubuntu. But permission not granted. Pls help
thanks

---

### Post by gandaran on 2011-06-15
use a root gedit to edit root system files, type in terminal
```
gksu gedit
```
now you will be able to open the file in the root gedit and edit it.

---

### Post by seawolf167 on 2011-06-15
See gandaran's post for the solution; here is more information if you are interested - [RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by ajgreeny on 2011-06-15
It is always worth installing **nautilus-gksu**, as you can then right click on any file or folder in the right hand pane of nautilus and select "open as administrator"  A great time saver.

---

### Post by crazylinux on 2011-06-15
Hey,
I m installing a software in ubuntu. It asks for the path of installation directory to be created. I want to install in /mydir i.e. mydir under root but it is not able to create when this path name is given.

Is it not possible to create any directory under root?

---

### Post by WorMzy on 2011-06-15
> **crazylinux said:**
> Hey,
I m installing a software in ubuntu. It asks for the path of installation directory to be created. I want to install in /mydir i.e. mydir under root but it is not able to create when this path name is given.

Is it not possible to create any directory under root?

Not as "your user", no. To create files and directories outside of your home folder, you need to be "root". On Ubuntu, you can temporarily become "root" by using "sudo". See seawolf's link for more information.

---

### Post by jocko on 2011-06-15
To do anything outside of your own user's home directory, you need to do it as root.
In ubuntu, to get root access you put "sudo" in front of the command (or gksu for graphical applications).

---

