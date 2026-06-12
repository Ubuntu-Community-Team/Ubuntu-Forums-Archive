---
title: "need help with sudo"
date: 2006-01-25
forum: General Help
---

### Post by cooldudejz on 2006-01-25
i recently tried to change my superuser password by usng this command "sudo passwd root" it didnt work and instead it seems to have disabled it. when i try to mount a hard drive it aks for the password, but when i run synaptic, firestarter and others it does not ask for a password. it also does not ask for a password when i run the sript "open as root." what did i do wrong. any help to return my computer to ins previous state. thanx

---

### Post by o_fortuna on 2006-01-25
[QUOTE=cooldudejz]i recently tried to change my superuser password by usng this command "sudo passwd root" it didnt work and instead it seems to have disabled it. when i try to mount a hard drive it aks for the password, but when i run synaptic, firestarter and others it does not ask for a password. it also does not ask for a password when i run the sript "open as root." what did i do wrong. any help to return my computer to ins previous state. thanx[/QUOTE]
What you did with "sudo passwd root" is enable the root account and give it a password. That's not what you wanted, since the sudo password is in fact **your** password (see this: [RootSudo]("https://wiki.ubuntu.com/RootSudo?highlight=%28rootsudo%29") )
To undo the changes, enter this in the terminal:
```
sudo passwd -l root
```
Now root will be inaccessible. To change your sudo password (ie, your password) do this at a terminal:
```
sudo passwd <USERNAME>
```
Where <USERNAME> is, of course, your own user name. And make sure you log in as that user, and use that password. That *should* fix your problem. If not, post back.

---

### Post by aysiu on 2006-01-25
Did you happen to do an expert install?

---

### Post by cooldudejz on 2006-01-25
i did not do an expert intsall.

---

