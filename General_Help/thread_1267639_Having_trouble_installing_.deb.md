---
title: "Having trouble installing .deb"
date: 2009-09-16
forum: General Help
---

### Post by PostChache on 2009-09-16
Hi, I've been having trouble installing this [http://maketecheasier.com/create-install-your-own-usplash-theme-in-ubuntu/2009/01/25](http://maketecheasier.com/create-install-your-own-usplash-theme-in-ubuntu/2009/01/25)

But when I get to [splashy_0.3.13-3ubuntu1_amd64.deb]("http://alioth.debian.org/frs/download.php/2712/splashy_0.3.13-3ubuntu1_amd64.deb") to install I get this error

Sorry for it being in spanish



```
 sudo dpkg -i /home/cha-che/Desktop/splashy_0.3.13-3ubuntu1_amd64.deb
(Leyendo la base de datos ...  
119547 ficheros y directorios instalados actualmente.)
Desempaquetando splashy (de .../splashy_0.3.13-3ubuntu1_amd64.deb) ...
dpkg: error al procesar /home/cha-che/Desktop/splashy_0.3.13-3ubuntu1_amd64.deb (--install):
 intentando sobreescribir `/etc/lsb-base-logging.sh', que está también en el paquete lsb-base
Procesando disparadores para man-db ...
Se encontraron errores al procesar:
 /home/cha-che/Desktop/splashy_0.3.13-3ubuntu1_amd64.deb


```

Okay I found this [https://bugs.launchpad.net/ubuntu/+source/splashy/+bug/391888](https://bugs.launchpad.net/ubuntu/+source/splashy/+bug/391888) so it's an existing error so could someone help me get rid of the other .deb? so I can install usplash again

---

### Post by running_rabbit07 on 2009-09-16
Go to Applications>System Tools>GDebi Package Installer. Does that install it?

---

### Post by PostChache on 2009-09-16
> **running_rabbit07 said:**
> Go to Applications>System Tools>GDebi Package Installer. Does that install it?
I do not have that in system tools I just have "configure-debian"

---

### Post by running_rabbit07 on 2009-09-16
> **PostChache said:**
> I do not have that in system tools I just have "configure-debian"

You may just need to add it to the menu via System>Preferences>Main Menu.

It should be there. I believe that GDebi is part of the factory install.

Once you get the program open. click File>Open and find the .deb you are trying to install.

---

### Post by PostChache on 2009-09-16
> **running_rabbit07 said:**
> You may just need to add it to the menu via System>Preferences>Main Menu.

It should be there. I believe that GDebi is part of the factory install.

Once you get the program open. click File>Open and find the .deb you are trying to install.
I got the same error D:

---

### Post by running_rabbit07 on 2009-09-16
> **PostChache said:**
> I got the same error D:

Darn. Hang in there and someone with more knowledge in error messages should help you out.

---

### Post by PostChache on 2009-09-16
> **running_rabbit07 said:**
> Darn. Hang in there and someone with more knowledge in error messages should help you out.
Okay thank you for your help.

---

