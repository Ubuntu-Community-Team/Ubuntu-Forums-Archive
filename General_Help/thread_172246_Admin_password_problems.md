---
title: "Admin password problems"
date: 2006-05-08
forum: General Help
---

### Post by ponytail on 2006-05-08
i got kubuntu installed on my laptop after a big fight with the cd..
but the computer was not connected to any network while installing. so now my ethernet and wireless are both disabled.. and i need to go to the admin mode to enable them.. but when it asks the password i put my user password from the first user account created during the install and it should be working i guess???
but no. it doesnt do anything.. 

so is there some default password anyway or whats the solution ?
i guess ill have the same problem with my soundcard soon..

thanks

---

### Post by Al3xanR0 on 2006-05-08
[QUOTE=ponytail]i got kubuntu installed on my laptop after a big fight with the cd..
but the computer was not connected to any network while installing. so now my ethernet and wireless are both disabled.. and i need to go to the admin mode to enable them.. but when it asks the password i put my user password from the first user account created during the install and it should be working i guess???
but no. it doesnt do anything.. 

so is there some default password anyway or whats the solution ?
i guess ill have the same problem with my soundcard soon..

thanks[/QUOTE]

If you are adventurous then do this

```
sudo passwd root
```

then add your userid to /etc/sudoers file to make kdesu happy especially for gui apps like Adept or Synaptic that require root access.

If not then just use sudo when you need to perform an administrative task.

---

### Post by aysiu on 2006-05-08
It's a KDE 3.4 bug that's been fixed for KDE 3.5.

You click the administrator mode button, type in your password, and then you don't get administrator mode.

The way around this is to press Alt-F2 and type ```
kdesu kcontrol
``` Type your password in, and you'll be in administrator mode.

---

### Post by mayhemt on 2006-05-08
Heres another dirty method:
do this
$sudo passwd
(same as above $sudo passwd root, basically u r changing the root passwd & remmbr that password )

& then do something like this
```
 mrt@Bluhills:~$ sudo nano /etc/kde3/kdm/kdmrc 
```

go to the place where you see this
```
 
# Allow root logins?
# Default is true
AllowRootLogin=false


```
& change  that to true, reboot & you can login as root, use password set above- now you need not do sudo or kdesu at all, but as they say, this is much unsecured dirty way, good for long configuration sessions.

---

