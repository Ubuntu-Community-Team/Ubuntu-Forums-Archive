---
title: "Dependency packages"
date: 2006-04-20
forum: General Help
---

### Post by kitts on 2006-04-20
Hi.
     I succeeded in the installation only yesterday..help me with the applications..

whenever i try to install any new program ..the installation fails..says some dependency packages need to be installed . When i install them they say they need some other packages. Is there an end to this? Can i install a simple program from the terminal using 'dpkg -i program.deb'.
           i tried yahoo messenger, opera 8.5,Myth Tv..all failed..
is there a way i can update these packages without the need of my involvement at every stage.:???:

---

### Post by Robgould on 2006-04-20
You should use Synaptic whenever possible, it will resolve the dependencies for you.  If you install a program you get from somwhere else that is not a .deb or you build from source you will have to handle dependencies yourself.  You will also have to worry about upgrades breaking your program.

---

### Post by cgjones on 2006-04-20
If you are looking for a command line option for installing programs that will handle dependencies, try apt-get.
```
apt-get install *program-name*
```

---

### Post by az on 2006-04-20
[QUOTE=kitts]Hi.
     I succeeded in the installation only yesterday..help me with the applications..

whenever i try to install any new program ..the installation fails..says some dependency packages need to be installed . When i install them they say they need some other packages. Is there an end to this? Can i install a simple program from the terminal using 'dpkg -i program.deb'.
           i tried yahoo messenger, opera 8.5,Myth Tv..all failed..
is there a way i can update these packages without the need of my involvement at every stage.:???:[/QUOTE]

Do not install stuff with dpkg.  Use apt (or any apt-frontend like synaptic, adept, or Add/Remove applications.  Dpkg is a low-level portion of the package manager.

As described in the help screen you see when you first launch synaptic, you need to add repositories to access a larger number of ubuntu applications.

---

### Post by brentroos on 2006-04-22
*

---

### Post by kitts on 2006-04-23
Ok This is the first error message i get when i tried ur command
**'sudo apt-get install libssl0.9.6 libgdk-pixbuf2'**
> root@kitts:~# sudo apt-get install libssl0.9.6 libgdk-pixbuf2
Reading package lists... Done
Building dependency tree... Done
libssl0.9.6 is already the newest version.
Package libgdk-pixbuf2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgdk-pixbuf2 has no installation candidate
root@kitts:~#


---

### Post by brentroos on 2006-04-24
*

---

### Post by adamkane on 2006-04-24
To avoid dpkg dependency hell, you should save all your deb files into a directory on your machine and create a local repository with autorepo. Then use apt to install everything, even local deb files.

No more missing dependencies this way.

---

