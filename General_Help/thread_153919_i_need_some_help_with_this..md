---
title: "i need some help with this."
date: 2006-04-02
forum: General Help
---

### Post by Mellon on 2006-04-02
i just install fedora, then trying to mount my ubuntu home (hda1)
it say i cant read couse im not root, so i change the owner of hda1 to my fedora  user, all worked fine.

but now, when i tray to use ubuntu, i have some problems about file atributes.
i get into rescue mode and type chown "user" -R / and now i can use ubuntu again. :-k 

is the a way to get back all my default files atributes, so i dont have to reinstall all again?

---

### Post by intel on 2006-04-02
You should not have changed the permissions of a whole linux installation.
You should have just mounted them as root. Whenever you need to access
a protected file, become root(then cp the file to your ~).

Now that it is all said and done, unless you have backup of that partition, 
REINSTALL will save you time & hair

---

### Post by Mellon on 2006-04-02
o well, ill reinstall later. using automatix ill save some time...

---

