---
title: "Moving /home"
date: 2006-04-19
forum: General Help
---

### Post by stabface on 2006-04-19
Hi, I have a Ubuntu server with a partion set up like 
/ 
/swap
/var

home was placed in / and i need to move it to /var because i am out of room 

i have gotten this far. 

mkdir /var/home
cp -a /home/* /var/home

now I am not sure what  should do can i just create a symbolic link between them and if so what is the right way to do that 

or do i need to edit other files?

---

### Post by colo on 2006-04-19
You'll be finde with the symbolic link alone. It's dirty, but it works.

You may want to consider using LVM2 (or EVMS with LVM2) for future setups.

---

### Post by stabface on 2006-04-20
i am not really sure what lvm does really, I tried it once and thought it was causing problems so i reformated normally, but this is a server that i made out of an extra pc

---

### Post by DoktorSeven on 2006-04-20
**man usermod**

```
sudo usermod -d /var/home/youruser -m youruser
```

---

### Post by David Olivier on 2006-04-20
Also, for a graphical interface:

System -> Administration -> Users and Groups

Find your username and click on Properties. Change the home directory.

Perhaps it would actually be enough to just change the home directory indicated in /etc/passwd but I wouldn't be sure.

---

