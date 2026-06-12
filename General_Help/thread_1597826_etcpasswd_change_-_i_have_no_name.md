---
title: "/etc/passwd change - i have no name"
date: 2010-10-15
forum: General Help
---

### Post by kesava_V on 2010-10-15
HI! I accidentally copied a /etc/passwd file to a wrong host from a source computer.

Now I am locked out( of root/ su/ sudo  privileges) and my terminal shows:

I have no name!@alladin:~$ sudo
sudo: unknown uid: 1000
I have no name!@alladin:~$ su
su: Cannot determine your user name.
I have no name!@alladin:~$ su root
su: Cannot determine your user name.
I have no name!@alladin:~$ 


I need some help on this please. I tried to change the file permissions but the root is not recognized.I need some serious help.

thank you.

---

### Post by luvshines on 2010-10-15
I think you can access your file using a Live CD and make changes.
But, I think you can wait for some expert comments to arrive before you loose this terminal which you have posted.

---

### Post by sisco311 on 2010-10-15
> **luvshines said:**
> I think you can access your file using a Live CD and make changes

+1

The backups of the file are: /etc/passwd- and /var/backups/passwd.bak*

The default owner and group of the file is **root**, **rw** permissions for the owner and **r** permission for the group and others.

EDIT: Oh, and welcome to the forums! [noparse]:)[/noparse]

---

### Post by kesava_V on 2010-10-16
HI luvshines and sisco311. thank you for the inputs.  much appreciate them!


I just tried something ... i logged in as a user and then su using ssh. the machine / linux let me in , and let me be the su on it .

i was able to change it  back remotely, have to test it now.will keep you posted !

---

### Post by luvshines on 2010-10-16
> **kesava_V said:**
> I just tried something ... i logged in as a user and then su using ssh. the machine / linux let me in , and let me be the su on it .

i was able to change it  back remotely, have to test it now.will keep you posted !

Gud that you are able to login with SSH but I think it's weird too :D
If /etc/passwd file has been overwritten, system will not be able to find any valid users and won't allow ssh even :confused:
Looks like the file is still usable, just a part of it has been messed up.

Newayz, GOOD LUCK !!

---

