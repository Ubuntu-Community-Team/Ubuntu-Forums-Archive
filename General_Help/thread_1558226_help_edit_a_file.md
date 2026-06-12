---
title: "help edit a file"
date: 2010-08-21
forum: General Help
---

### Post by cschamber on 2010-08-21
im trying to install an internet dj'ing prog but it saies i need to manualy add some lines of code in my limits.config, i find the file and open it and try to type, and i get nothing . so i right click and try to change the read only permissions so i could write also, and it sais i have to be the owner to change that setting, but i am the computer owner and i am logged in to my only profile so i should have full access rights, attached is a screen shot of the problem and the 2 lines of codr i need to add to that file ( there in the terminal window) can some one tell me if i am doing somthing wrong, ive only been on ubuntu for a few months so im by far no brainiack on it....... yet

---

### Post by cschamber on 2010-08-21
for got to add screen shot tp original post so its attached to this one

---

### Post by lordskid on 2010-08-21
you have to open a terminal and do a sudo chown name:group filename

e.g. if your username is cschamber
```

sudo chown cschamber:cschamber limits.config

```

or the easiest way would be to sudo gedit limits.config

---

### Post by jcolyn on 2010-08-21
If you don't have gedit installed go to the terminal and type ```
sudo apt-get install gedit
```

Once installed again open the terminal and type ```
sudo gedit limits.conf
```

This will give you temp root rights to edit the file..

---

### Post by earthpigg on 2010-08-21
the posts above me are correct. however,

> **cschamber said:**
>  so i right click and try to change the read only permissions so i could write also, and it sais i have to be the owner to change that setting,

in the future, you could also run nautilus (the file manager) as root to take care of the permission issue.

```
gksudo nautilus
```

---

