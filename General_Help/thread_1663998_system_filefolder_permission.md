---
title: "system file/folder permission"
date: 2011-01-10
forum: General Help
---

### Post by Milan Mendpara on 2011-01-10
:KS    there is only one user in my system with** account type = Administrato**r ... 
but still i'm not able to change or copy file in file system folder.
         is there any way to do copy or change in system folder/file ...... :confused:

[LEFT]
[/LEFT]

---

### Post by hayhursm on 2011-01-10
> **Milan Mendpara said:**
> :KS    there is only one user in my system with** account type = Administrato**r ... 
but still i'm not able to change or copy file in file system folder.
         is there any way to do copy or change in system folder/file ...... :confused:

[LEFT]
[/LEFT]


You need superuser powers aka "sudo" to change the File System.  If you use Nautilus, go to File System, right click on a folder, click Properties, then click Permissions tab it probably lists Root.

---

### Post by endotherm on 2011-01-10
ok, first off, as you work with linux, you will find yourself doing very little to the root partition and its file structures. on the occassions that you do, its a good thing that admin is required. just store your personal files in your home or in a data drive that you own. 

when you do need to work with the root filesystem, you can run nautilus or a terminal as root to make it easier. to open nautilus as admin, hit Alt + F2 and enter
```
gksu nautilus
``` (gksu is sudo for graphical apps), or install the package "[nautilus-gksu]("http://www.liberiangeek.net/2010/09/add-open-administrator-nautilus-context-menu-ubuntu-10-10-maverick-meerkat/")"

for terminal, check here:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Milan Mendpara on 2011-01-10
is it work on ubuntu 10.04 ?

---

### Post by endotherm on 2011-01-10
yep. that hasn't changed in some time.

---

### Post by Milan Mendpara on 2011-01-10
ok thx for your suggestions ...:)

---

