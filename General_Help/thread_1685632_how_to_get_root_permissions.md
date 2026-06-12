---
title: "how to get root permissions?"
date: 2011-02-11
forum: General Help
---

### Post by debd on 2011-02-11
I need to add some files in /usr/local/include
but the folder properties says "you are not the owner" :o
I guess I have to be root to perform it.
now how do I get root permissions to copy files to that folder using Nautilus?
using the terminal would be a bit of messy..

---

### Post by Krytarik on 2011-02-11
Press Alt+F2 and enter "gksudo nautilus", when asked enter your password.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by debd on 2011-02-11
thanks man.

that worked.

 but I wanted geany (an IDE) to able to work with files in that directory....but it says "permission denied" for accessing the necessary file. do I have to run Geany with root privilages to do it??

---

