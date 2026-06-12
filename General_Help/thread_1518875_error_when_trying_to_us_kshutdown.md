---
title: "error when trying to us kshutdown"
date: 2010-06-27
forum: General Help
---

### Post by wpshooter on 2010-06-27
I am trying to use KSHUTDOWN to do an automated shutdown of my Ubuntu computer but getting error message that says that "**kshutdown could not** **contact session manager**".

What is problem ?

Thanks.

---

### Post by dragos240 on 2010-06-27
> **wpshooter said:**
> I am trying to use KSHUTDOWN to do an automated shutdown of my Ubuntu computer but getting error message that says that "**kshutdown could not** **contact session manager**".

What is problem ?

Thanks.

You're not using KDM, you're most likely using GDM, the default login manager. Do this in a terminal:
sudo dpkg-reconfigure kdm

if kdm is not installed do this:
sudo apt-get install kdm

---

### Post by wpshooter on 2010-06-27
> **dragos240 said:**
> You're not using KDM, you're most likely using GDM, the default login manager. Do this in a terminal:
sudo dpkg-reconfigure kdm

if kdm is not installed do this:
sudo apt-get install kdm

When I do that first line it comes back and say KDM is not installed, which is correct, it is not and **I don't want it to be**.

Will this KSHUTDOWN only work if you are running KDE interface instead of GNOME ?

Thanks.

---

### Post by dragos240 on 2010-06-27
> **wpshooter said:**
> When I do that first line it comes back and say KDM is not installed, which is correct, it is not and **I don't want it to be**.

Will this KSHUTDOWN only work if you are running KDE interface instead of GNOME ?

Thanks.

Sorry it won't. KDE is very peticular, KDM is your only option if you want native shutdowns in KDE.

---

