---
title: "Error installing wine"
date: 2010-01-08
forum: General Help
---

### Post by BAleR187 on 2010-01-08
I'm having an issue installing wine, it gives me an error, correct me if im wrong but dont i need to be singed in as root? When i open terminal and type in su root, and type in the pass alpine, which is the defult right? it says its wrong. ? also i have no internet through ubuntu so i cant install through the repo, i have to manually install, thanks for any help

---

### Post by HiImTye on 2010-01-08
the root account is disabled for security. you access the root account using sudo

i.e.
```
sudo apt-get install <package>
```or
```
gksudo gedit
```for graphical programs

if you're installing a .deb you should be able to double click it. you will need to make sure you have all dependencies met, however

edit: sudo asks for _your_ password (you need to be an administrator)

---

### Post by BAleR187 on 2010-01-08
> **HiImTye said:**
> the root account is disabled for security. you access the root account using sudo

i.e.
```
sudo apt-get install <package>
```or
```
gksudo gedit
```for graphical programs

if you're installing a .deb you should be able to double click it. you will need to make sure you have all dependencies met, however

edit: sudo asks for _your_ password (you need to be an administrator)




ok i see now, how will i check the dependencies?

---

### Post by HiImTye on 2010-01-08
the package manager will tell you if you don't have any. also, the [ubuntu download site]("http://packages.ubuntu.com/karmic/wine") lists the dependencies. if you are using a different version of ubuntu, change it at the top of the page (that link is for karmic (9.10))

---

### Post by BAleR187 on 2010-01-08
[quote=HiImTye;8629753]the package manager will tell you if you don't have any. also, the [ubuntu download site]("http://packages.ubuntu.com/karmic/wine") lists the dependencies. if you are using a different version of ubuntu, change it at the top of the page (that link is for karmic (9.10))[/quo


ok thank you for helping, and yes that is the version i have, i downloaded it today burnt it on a disk and installed it fine, another thing, i have a geforce 9400 gt vid card and when i go to the drivers manager it doesnt have any drivers displayed to configure, whats up with that?

---

