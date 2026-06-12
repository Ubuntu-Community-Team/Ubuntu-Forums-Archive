---
title: "the superuser"
date: 2006-05-29
forum: General Help
---

### Post by D_block on 2006-05-29
hi guys i-m a noob i-m trying to get away from windows so i have a prob. in the console i try to install a prog in .deb format, i use the command dpkg -i and the name of the program and it says that i need superuser privilege, someone told me to create an account named superuser and the profile>administrator and edit, mark all that i see in reference to an administrator, log out and log in as superuser, in the console i try the same command loged as superuser too and still it says that i need superuser privilege pls people help me, thax to all that will post

---

### Post by tkjacobsen on 2006-05-29
to run a command as superuser, type sudo before the command:
```
sudo dpkg -i packagename.deb
```
A better description of how to use the superuser: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)


Before installing a package like this, see if it is in synaptic (system -> administration -> synaptic package manager) This is the common way of installing new software in ubuntu. 

To get extra software se this howto:
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by D_block on 2006-05-29
thanx, only it displays an error and says cannot access archive:no such file or directory and in the synaptic, there isnt the program i am looking for btw thanx very much

---

