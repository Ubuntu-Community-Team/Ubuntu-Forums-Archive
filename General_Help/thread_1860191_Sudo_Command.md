---
title: "Sudo Command"
date: 2011-10-14
forum: General Help
---

### Post by spiky001 on 2011-10-14
Hi I know about running as root and how to use sudo, and sudo will work for a set time without password. I would like to know how to run sudo without the password popping up, ( i dont want/need a permenant change) Just while I work on a external drive to run root commands, i dont want to change ownership of the drive either. Just to put it plain run as sudo/root then be able to exit. Is this possible.   Or would it be possible to start a terminal that is root so when you exit the terminal privalages are returned as normal?

---

### Post by NoNameWill on 2011-10-14
> **spiky001 said:**
> Hi I know about running as root and how to use sudo, and sudo will work for a set time without password. I would like to know how to run sudo without the password popping up, ( i dont want/need a permenant change) Just while I work on a external drive to run root commands, i dont want to change ownership of the drive either. Just to put it plain run as sudo/root then be able to exit. Is this possible


```
sudo su
```

This works in 11.04/10 

This will give you root privilege.

---

### Post by collisionystm on 2011-10-14
or sudo bash

---

### Post by effenberg0x0 on 2011-10-14
[http://askubuntu.com/questions/64178/why-sudo-s-is-better-than-sudo-su](http://askubuntu.com/questions/64178/why-sudo-s-is-better-than-sudo-su)

sudo -s keeps your $HOME environment variable set. Meaning that when you run the system without being root, programs will be able to access your settings saved in folders/files in your home directory. 

If you make changes to settings (or the programs you run make changes to settings) and save them to /root folder and files, they won't be there when you're logged in as a normal user.

Regards,
Effenberg

---

### Post by spiky001 on 2011-10-14
```
sudo gnome-terminal bash &
``` Dose the exact job I want thks for pointing me in right direction

---

### Post by spiky001 on 2011-10-14
It,s not for running on Ubuntu system but another system LFS which needs root and user to install programs

---

