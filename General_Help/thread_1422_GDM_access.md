---
title: "GDM access?"
date: 2004-10-20
forum: General Help
---

### Post by Vulc on 2004-10-20
how am I supposed to access gdm without a root account? it keeps asking me for the root password and I don't know what to do  :cry:

---

### Post by JProgrammer on 2004-10-20
Ubuntu doesn't have a root account yes but you do everything with sudo so there is root privileges.... the root password is the same as the password for the user you setup during install

---

### Post by williamroddy on 2004-10-21
Being old fashioned, the first thing I did was open up the terminal, type:

sudo passwd root

and create a root password.

First, it asks for your pasword. Then, it asks for the new root password.

I'm a creature of habit and like to have root access this way. The nice thing is, Ubuntu is flexible and will let you do things your way.

Toward peace,
Wil

---

### Post by Burgundavia on 2004-10-21
To correct Jprogrammer, there is no root password in Ubuntu by default. Ubuntu uses a program called sudo, also called super-user do, with runs the program as root. The password they are asking for is your password, as a security measure. 

And as for the second option, I would not recommend it for a novice Linux user. You can seriously mess up your computer. Sudo is much safer, IMHO.

Corey

---

