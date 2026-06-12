---
title: "Problems with PXESCONFIG AND UBUNTU"
date: 2006-03-08
forum: General Help
---

### Post by PeraKus on 2006-03-08
Hello,

I have a problem on having tried to install pxesconfig, I lack the following parts:

lade-perl (>= 0.60) --->  Not found 
    Convert Glade-Interface XML into perl code

[dep] hwdata --->  OK 
    hardware identification / configuration data

[dep] libgnome-perl (>= 0.7000)   --_> Not found  but it have Libgnome2
    Perl module for the gnome and zvt libraries

[dep] mkisofs  --_> Instalado
    Creates ISO-9660 CD-ROM filesystem images

[dep] mknbi   --> Not found 
    Create tagged images for Etherboot or Netboot

[dep] pxes (= 0.7-1-1)   ---->  Not found 

The error to use this comand:  dpkg -i pxesconfig_0.7-1-3_all.deb

  (S'està llegint la base de dades ... hi ha 71348 fitxers i directoris instal·lats actualment.)
  S'està desempaquetant pxesconfig (de pxesconfig_0.7-1-3_all.deb) ...
  dpkg: problemes de dependències impedeixen la configuració de pxesconfig:
  
pxesconfig depèn de pxes (= 0.7-1-1); tot i així:
  el paquet pxes no està instal·lat.
 
 pxesconfig depèn de libgnome-perl (>= 0.7000); tot i així:
  el paquet libgnome-perl no està instal·lat.
  pxesconfig depèn de glade-perl (>= 0.60); tot i així:
  
  el paquet glade-perl no està instal·lat.
  pxesconfig depèn de mknbi; tot i així:

  el paquet mknbi no està instal·lat.
  
  dpkg: s'ha produït un error en processar pxesconfig (--install):
  problemes de dependències - es deixa sense configurar
  S'han trobat errors en processar:
  pxesconfig

I need help to find i to install these packages
Thanks ! 

Linux Power ! \\:D/

---

