---
title: "Problems with DraftSight in ubuntu 10.04.4 64bits,"
date: 2012-02-15
forum: General Help
---

### Post by AnotherOneMore on 2012-02-15
Can anyone help me please?

I have the following problem installing DraftSight:

miguel@miguel-laptop:~$ sudo dpkg -i --force-architecture '/home/miguel/Downloads/draftSight.deb'
[sudo] password for miguel: 
dpkg: warning: overriding problem because --force enabled:
 la arquitectura del paquete (i386) no corresponde con la del sistema (amd64)
(Leyendo la base de datos ...  00%
309901 ficheros y directorios instalados actualmente.)
Preparando para reemplazar dassault-systemes-draftsight 2012.1.1177 (usando .../Downloads/draftSight.deb) ...
access control disabled, clients can connect from any host
access control disabled, clients can connect from any host
access control enabled, only authorized clients can connect
access control enabled, only authorized clients can connect
Desempaquetando el reemplazo de dassault-systemes-draftsight ...
Configurando dassault-systemes-draftsight (2012.1.1177) ...
Set application as default for the user=miguel
mkdir: cannot create directory `/home/miguel/.kde': Permission denied
touch: cannot touch `/home/miguel/.kde/share/config/profilerc': Permission denied
/usr/bin/xdg-mime: line 520: /home/miguel/.kde/share/config/profilerc.new: Permission denied
Set application as default for the user=miguel
mkdir: cannot create directory `/home/miguel/.kde': Permission denied
touch: cannot touch `/home/miguel/.kde/share/config/profilerc': Permission denied
/usr/bin/xdg-mime: line 520: /home/miguel/.kde/share/config/profilerc.new: Permission denied
Set application as default for the user=miguel
mkdir: cannot create directory `/home/miguel/.kde': Permission denied
touch: cannot touch `/home/miguel/.kde/share/config/profilerc': Permission denied
/usr/bin/xdg-mime: line 520: /home/miguel/.kde/share/config/profilerc.new: Permission denied

---

### Post by imachavel on 2012-02-15
have you tried sudo apt-get install draftsight0.0 ?(replace with actual version)

I have never downloaded draft sight, I tried using a different cad though, and forgot the name of it, but it was pretty bad ***, I'll have to look around for it again

this video looks pretty cool though:

[http://www.3ds.com/products/draftsight/overview/latest-release/](http://www.3ds.com/products/draftsight/overview/latest-release/)

---

### Post by AnotherOneMore on 2012-02-16
Thank you for your help, but it did not work. 

I think I tried all the cad avaliables for ubuntu, and DraftSight is the best by far!

---

