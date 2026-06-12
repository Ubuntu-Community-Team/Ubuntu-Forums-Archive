---
title: "folder help and understanding the layout"
date: 2009-07-10
forum: General Help
---

### Post by e24ohm on 2009-07-10
Folks:
can someone explain what are all the folders used for in "/"? I am coming from the windows world, and which folder is used as "program files"?

If i install an application, where will it install? For example: etc, usr, etc.

thank you.
E

---

### Post by Cheesemill on 2009-07-10
Check out this link:
[http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/)

Also if you want to find out where a particular application is install you can use the which command, for example:
```
which firefox
```
will return
```
/usr/bin/firefox
```

---

### Post by wojox on 2009-07-10
Filesystem Hierarchy Standard:

[http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)

Also Ubuntu Pocket Guide and Reference:

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by geirha on 2009-07-10
To see where a package installed its files, you can run
```
dpkg -L *packagename*
# E.g. for firefox-3.0
dpkg -L firefox-3.0

```
As you can see, the files are spread around the filesystem depending on their purpose; as opposed to windows where all files belonging to a program gets installed in the same directory.

---

### Post by credobyte on 2009-07-10
**/** - in Windows world, known as C:/
**/etc** - in Windows world, know as Program Files

Links posted above will give you more information ;)

---

### Post by e24ohm on 2009-07-10
folks,
thanks for this help...this has helped a great deal. I was looking for a config file the other day and had no clue where it was. Maybe now i can find it.

---

