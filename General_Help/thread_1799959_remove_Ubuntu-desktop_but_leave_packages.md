---
title: "remove Ubuntu-desktop but leave packages"
date: 2011-07-08
forum: General Help
---

### Post by elliotn on 2011-07-08
I have Ubuntu and kubuntu-desktop installed. I want to remove ubuntu-desktop but leave its packages like Firefox, banshee etc, I like those apps but am afraid they will go if I remove Ubuntu.

---

### Post by dino99 on 2011-07-08
both are meta-packages (list of packages links) and they remove nothing if you purge them, dont worry.

---

### Post by mikejonesey on 2011-07-08
[SIZE=1][STRIKE]only trouble is you may well break a whole load of things doing this, it goes against how package managers work...;

```
apt-cache depends ubuntu-desktop | grep -i depends:
```will list all files that would be removed...[/STRIKE][/SIZE] 

why do you want to remove this package? it's disk size is faily small (more of a place holder for dependants...)

```
dpkg -L ubuntu-desktop
```(not much to remove...)

update: woops that was bad info

---

### Post by elliotn on 2011-07-08
ok I will keep it and just change the gdm to kubuntu

thanks

---

