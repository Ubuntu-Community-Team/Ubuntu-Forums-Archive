---
title: "Running an already installed problem with wine"
date: 2011-11-24
forum: General Help
---

### Post by Horfan on 2011-11-24
I'm currently running a setup with Windows 7 on one partition and Ubuntu on another. Yesterday windows started acting up so I switched to ubuntu until i can be arsed to fix it.  I've got everything i need on ubuntu except for skyrim which i have installed on windows and, is it possible to run it through wine? I'm asking because I tried just clicking on the .exe but it told me i had to mark it as executable but it won't let me change the permission.

---

### Post by notgary on 2011-12-04
If you can access the Windows partition, then you could try copying the Skyrim system files out of the Program Files directory on Windows into the corresponding directory inside Wine, then try again to run the .exe file. I'm not sure if that'll work, it's just a pie in the sky idea.

---

### Post by digithal on 2011-12-04
Open terminal, navigate to your Skyrim directory and type:
```
wine SkyrimLauncher.exe
```
or whatever is the game exe called :)

---

### Post by *^kyfds( on 2011-12-04
> **Horfan said:**
> I'm currently running a setup with Windows 7 on one partition and Ubuntu on another. Yesterday windows started acting up so I switched to ubuntu until i can be arsed to fix it.  I've got everything i need on ubuntu except for skyrim which i have installed on windows and, is it possible to run it through wine? I'm asking because I tried just clicking on the .exe but it told me i had to mark it as executable but it won't let me change the permission.

i thought you needed steam to launch skyrim 0_0

assuming you still have the disc, have you tried reinstalling on ubuntu?

---

### Post by Mark Phelps on 2011-12-04
I would be very surprised if ANYTHING you did along these lines actually worked!  Why?

Because Windows apps (nearly always) rely critically on values stored in the "registry" to work -- and the registry contained in your NATIVE Windows system is entirely separate from the registry contained in Wine -- which is WHY, apps have to be installed in Wine to work.

---

### Post by oldtimer7777 on 2011-12-04
I use VMWare Player and have it seamlessly integrated into my Ubuntu desktop like this:

[https://debianhelp.wordpress.com/2011/11/22/how-to-install-vmware-player-in-ubuntu/](https://debianhelp.wordpress.com/2011/11/22/how-to-install-vmware-player-in-ubuntu/)

Wine is very good for tiny apps..  But you need the real deal here. 

> **Mark Phelps said:**
> I would be very surprised if ANYTHING you did along these lines actually worked!  Why?

Because Windows apps (nearly always) rely critically on values stored in the "registry" to work -- and the registry contained in your NATIVE Windows system is entirely separate from the registry contained in Wine -- which is WHY, apps have to be installed in Wine to work.

---

