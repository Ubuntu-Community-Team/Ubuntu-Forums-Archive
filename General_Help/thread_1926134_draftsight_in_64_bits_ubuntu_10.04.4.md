---
title: "draftsight in 64 bits ubuntu 10.04.4"
date: 2012-02-15
forum: General Help
---

### Post by AnotherOneMore on 2012-02-15
[ubuntu] draftsight installation problems in 64 bits

Please help me, I can not install draftsigth, it is returned:

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

