---
title: "2 problems"
date: 2006-05-06
forum: General Help
---

### Post by crakkajakka15 on 2006-05-06
Ok i got two issues i need addressed please. 1 is that i cant seem to find out how to update my kernel in kubuntu. Like in ARCH linux i just go to the console and type pacman -Syu and it updates everything, how can i do that on kubuntu, exspecially for the kernel update. 2 is i downloaded a game called cube looks really kool but i cant for the life of me get it to install, ive been to the terminal and did the whole sudo apt-get install........ thing and it says E: cant find package.... please help 
Thanks Again
Todd

---

### Post by aysiu on 2006-05-06
It's not in the repositories.
You'll have to compile from source for that one.

By the way, I'm referring to *cube*.

---

### Post by tseliot on 2006-05-06
```
pacman -Sy = sudo apt-get update

pacman -Syu = sudo apt-get update && sudo apt-get dist-upgrade

pacman -Ss = sudo apt-cache search
```


to install a deb package (not from the repos):
```
sudo dpkg -i name_of_the_package.deb
```

---

### Post by crakkajakka15 on 2006-05-06
[QUOTE=tseliot]```
pacman -Sy = sudo apt-get update

pacman -Syu = sudo apt-get update && sudo apt-get dist-upgrade

pacman -Ss = sudo apt-cache search
```


to install a deb package (not from the repos):
```
sudo dpkg -i name_of_the_package.deb
```[/QUOTE]



i did all the update commands above and it still didnt update the kernel i belive the kernel is on 2.6.16 right now and im running 2.6.12 any ideas?

---

### Post by ComplexNumber on 2006-05-06
[quote=crakkajakka15]i did all the update commands above and it still didnt update the kernel i belive the kernel is on 2.6.16 right now and im running 2.6.12 any ideas?[/quote] i update mu kernel on fedora. it may be a different distro, but the ideas and processes are still ther same.
-download the kernel deb package from the repositories, but don't install it just yet.
-uninstall all kernel modules (eg kerrnel-devel, kernel-xen, etc) until you are left with the kernel itself.
-log out and go into failsafe teminal (i don't think this is actually required. could probably still install new kernel in gnome/kde, but i wanted to install the kernel with minimum 'overhead'(eg not running the X server etc))
-cd to where the new kernel is located and updated. to install on fedora, i used the command 'rpm -Uvh kernel-2.6.16*'. i don't know what the equivelent dpkg command is to update because i'm much more familiar with rpm.
-rebooted. i noticed that when i rebooted, it showed the new kernel.

---

### Post by crakkajakka15 on 2006-05-06
where do i get the .deb kernel at to do this

---

### Post by crakkajakka15 on 2006-05-07
????

---

