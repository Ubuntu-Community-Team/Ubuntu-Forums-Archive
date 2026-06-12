---
title: "sudo apt get update no internet"
date: 2009-08-12
forum: General Help
---

### Post by MistaMista on 2009-08-12
is there ne way i can get these updates from a computer with internet connection n then install on my ubuntu os

---

### Post by pmlxuser on 2009-08-12
if the machine connected to the internet is an ubuntu machine with the same version as your offline machine. i found an easier way is to copy the /var/cache/apt/archives/ *.deb  to some folder lets say ubuntu-deb on desktop, transfer them to a flashdisk
go to the offline machine and copy the ubuntu-deb contents into the var/cache/apt/archives folder

however u should be sudo to do that. assuming you have cd in the folder then you execute the following command in terminal

```

user@user-machine/ubuntu-debs$ sudo cp *.deb /var/apt/cache/archives

```

if do a
```

 sudo apt-get -m upgrade 
```

you should be able to update your system.

its very difficult to update otherwise because you have to know the dependencies of each package by heart in order to make the feat.

---

### Post by Cheesemill on 2009-08-12
[FONT=Tahoma][http://keryxproject.org/](http://keryxproject.org/)[/FONT]

---

### Post by pmlxuser on 2009-08-12
+ 1 to Cheesemill and [http://keryxproject.org/](http://keryxproject.org/)

---

### Post by kambrik on 2009-08-12
[http://www.compuhowto.com/linux/ubuntu/ubuntu-update-with-no-internet/](http://www.compuhowto.com/linux/ubuntu/ubuntu-update-with-no-internet/)

---

