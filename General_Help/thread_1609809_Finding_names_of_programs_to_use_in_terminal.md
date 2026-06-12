---
title: "Finding names of programs to use in terminal"
date: 2010-10-30
forum: General Help
---

### Post by Jetso on 2010-10-30
I would like to know how to find out the name of programs so that I could launch them in Terminal. For example, to launch gimp, I just type ```
gimp
``` and it launches. Well how do I find out other names to other programs?

---

### Post by matsuzine on 2010-10-30
one simple way it to go to your Applications menu and right click.  Choose 'Edit Menus' then select the menu and the item you're interested in.  If you choose Properties, you can see the command that is used to start the application.  Don't make any changes, as this will goof up the menu item...

---

### Post by eric_1982 on 2010-11-01
Often you can look in /usr/bin

For example firefox , gnome-terminal ..etc

To get a list were most application reside you could look at the enviorment settings and look for something that says PATH= 

open a terminal and type **env**

look for something similar like 

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/real/RealPlayer

These are the paths were most applications will reside that allow you to type gimp instead of the full path such as  /usr/bin/gimp

---

