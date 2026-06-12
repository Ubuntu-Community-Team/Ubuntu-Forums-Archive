---
title: "autoremove wants to remove libreoffice?"
date: 2012-09-08
forum: General Help
---

### Post by claracc on 2012-09-08
Hello, I have a hp compaq 6720s laptop recently upgraded from 10.04 to 12.04.

I am using gnome fallback as desktop.

I had openoffice3.3 installed in my 10.04 system, when I upgraded to 12.04, libreoffice was installed too. So I decided to uninstall openoffice. I did it through synaptic.

I also removed a package named openoffice-ure- or something similar. Since then, if I run in a xterm the command:

sudo apt-get autoremove , I obtain:


> clara@clara1:~$ sudo apt-get autoremove
[sudo] password for clara: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Los siguientes paquetes se ELIMINARÁN:
  libreoffice libreoffice-filter-mobiledev openclipart-libreoffice
  openclipart-png ttf-sil-gentium-basic
0 actualizados, 0 se instalarán, 5 para eliminar y 0 no actualizados.
Se liberarán 682 MB después de esta operación.
¿Desea continuar [S/n]? n
Abortado.
clara@clara1:~$ 
 

Of course I abort the removal of libreoffice, I want to have it.

Why is this happening?, did I remove some dependency openoffice package affecting libreoffice?(all of what I removed has a name starting by openoffice). How can I fix it?

Thanks in advance

---

### Post by dcstar on 2012-09-08
> **claracc said:**
> Hello, I have a hp compaq 6720s laptop recently upgraded from 10.04 to 12.04.
..........
Why is this happening?, did I remove some dependency openoffice package affecting libreoffice?(all of what I removed has a name starting by openoffice). How can I fix it?

Thanks in advance

You may have to uninstall and then reinstall it to get your system fixed. It may be quicker than trying to find the missing piece.

---

### Post by claracc on 2012-09-08
Thanks dcstar, done.

I have uninstalled libreoffice, then run sudo apt-get autoremove, select yes, install again libreoffice and the problem is solved.

Now if I run sudo apt-get autoremove, I obtain:

> clara@clara1:~$ sudo apt-get autoremove
[sudo] password for clara: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
clara@clara1:~$ 


---

