---
title: "Problem with LightDM after selecting gdm as default login manager"
date: 2011-11-05
forum: General Help
---

### Post by dado_eyad on 2011-11-05
I installed GNOME 3 on Ubuntu 11.10 and in the install process I chose gdm as the login screen. I want to switch back to LightDM. I ran sudo dpkg-reconfigure gdm and chose LightDM but it gives me a black screen when I restart.

Help please

---

### Post by enkay009 on 2011-11-05
Check the contents of **/etc/X11/default-display-manager**

If you want to use lightdm, it's contents should be:
```
/usr/sbin/lightdm
```

---

### Post by dado_eyad on 2011-11-08
same problem

check this as it may help

```

eyad@eyad-laptop:~$ sudo dpkg-reconfigure gdm   
[sudo] password for eyad:    (I choose lightdm)
Please be sure to run "dpkg --configure lightdm".
eyad@eyad-laptop:~$ sudo dpkg --configure lightdm
dpkg: error processing lightdm (--configure):
 package lightdm is already installed and configured
Errors were encountered while processing:
 lightdm
eyad@eyad-laptop:~$ sudo dpkg-reconfigure lightdm  (I choose lightdm again although it's the on in used)
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_NAME missing
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_PACKAGE missing
eyad@eyad-laptop:~$ 


```

---

### Post by dado_eyad on 2011-11-13
no one knows?

---

### Post by Cyclane on 2011-11-13
Are you able to connect to the internet?

> sudo apt-get install --reinstall lightdm

---

### Post by dado_eyad on 2011-11-18
I am connected and I tried re installing and it's the same problem

---

### Post by rolfijn on 2011-11-27
For me the solution of enkay009 worked. After I changed the content of /etc/X11/default-display-manager from "lightdm" to "/usr/sbin/lightdm" a reboot resulted in a working lightdm. To do this on a system that doesn't boot, start the system and wait for it to "hang". Then press CTRL-ALT-F1 to get a virtual console and login with your user account. Type "sudo su"  to gain sufficient rights after entering your password. Then type "echo /usr/sbin/lightdm > /etc/X11/default-display-manager" to make the appropriate changes.

---

