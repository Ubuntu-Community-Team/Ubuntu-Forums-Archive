---
title: "update manager error - dpkg interrupted"
date: 2010-03-09
forum: General Help
---

### Post by rebster61 on 2010-03-09
Update manager gives the following error. 

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I have no idea how to run sudo dpkg manually - this is Ubuntu 9.1 on a windows xp system.

---

### Post by MelDJ on 2010-03-09
go to applications-accesories and open terminal.
there, type the following
```
sudo dpkg --configure -a
```press enter and type in your password at the prompt and press enter again

---

### Post by bumanie on 2010-03-09
Open terminal via Applications --> Accessories --> Terminal and type > sudo dpkg --configure -aand hit enter. You will then be asked for your password - type it and hit enter - broken packages should get fixed. Note that when you enter your password there is no visual output, but it will be registered.
I'm slow too!

---

### Post by MooPi on 2010-03-09
There is application called terminal to enter these commands. I believe it under the first menu Accessories/Terminal. Upon opening just type in the command ```
sudo dpkg --configure -a
``` and press enter. If you have trouble locating the terminal alt + F2 will open a run dialog and you can start terminal through that ```
gnome-terminal
```
 I'm to slow :-)

---

### Post by jbabe on 2010-03-14
I had the same problem - thanks this fixed it :)
Thanks.

---

