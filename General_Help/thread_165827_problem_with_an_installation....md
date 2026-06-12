---
title: "problem with an installation..."
date: 2006-04-25
forum: General Help
---

### Post by orlox on 2006-04-25
Hi, i'm trying to install a program on my xubuntu dapper, but I can't get it done...the program is IRAF, and in a step of the installation process, for wich you need to create a user acount named iraf, that uses a C-shell, you have to type on a terminal as the iraf user the following:

cat /home/pablo/iraf/intento/as.pcix.gen.gz | zcat | tar -xpf -

to wich I get the following erros of tar:

tar: ./local: No se puede utime: Operación no permitida
tar: ./local: No se puede cambiar el modo a rwxr-xr-x: Operación no permitida
tar: .: No se puede utime: Operación no permitida
tar: .: No se puede cambiar el modo a rwxr-xr-x: Operación no permitida
tar: Salida con error demorada desde errores anteriores

wich means something like


tar: ./local: Cannot utime:operation not permited
tar: ./local: Can't change the mode to rwxr-xr-x: operation not permited
tar: .:  Cannot utime: operation not permited
tar: .: Can't change the mode to rwxr-xr-x: operation not permited
tar: Exit with error delayed from previous errors

how am i supposed to give the iraf user the capability of performing this operations...

---

### Post by dg_w on 2006-04-25
Try

sudo cat /home/pablo/iraf/intento/as.pcix.gen.gz | zcat | tar -xpf -

---

### Post by orlox on 2006-04-25
That would be a solution, but isn't there a way to grant those "powers" to the iraf user account?

---

### Post by ssalman on 2006-04-25
Try adding sudo as below:

cat /home/pablo/iraf/intento/as.pcix.gen.gz | zcat | sudo tar -xpf

---

### Post by dg_w on 2006-04-25
Maybe this will help ?

[http://www.ubuntuforums.org/showthread.php?t=162867&highlight=add+user+sudo](http://www.ubuntuforums.org/showthread.php?t=162867&highlight=add+user+sudo)

Adding users to Sudo ?

---

### Post by orlox on 2006-04-25
weird...when using sudo as the iraf user, it promts me for my password, but it wont accept it!!! as any normal user there is no problem when doing that...

---

### Post by dg_w on 2006-04-25
When sudo as the iraf user, I think you should use the iraf user password ?
If unsure:
sudo passwd iraf

and set\reset the password :)

---

### Post by orlox on 2006-04-25
using passwd throws this at me:

root@pcpablo:/iraf/iraf# sudo passwd iraf
passwd: User not known to the underlying authentication module


????

I have the user included at the admin grup, and with the "executing sistem administration tasks" checkbox checked on the gui for modyfing the users...but it still wont work. Maybe it has something to do with the account running on csh instead of bash?

---

