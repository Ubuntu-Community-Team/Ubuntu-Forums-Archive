---
title: "Error al momento de instalar programas"
date: 2010-01-07
forum: General Help
---

### Post by Diegox on 2010-01-07
Cuando trato de instalar un programa o actualizar el sistema [Ubuntu 9.10] me sale un mensajito que dice: 

[B]E: ttf-dejavu-extra: el subproceso script post-installation instalado devolvió el código de salida de error 1
E: ttf-dejavu: problemas de dependencias - se deja sin configurar

[IMG]http://img189.imageshack.us/img189/6216/problemah.png[/IMG]

[/B]-.Ayudenme por favor, gracias de antemano.-

---

### Post by adam814 on 2010-01-07
Lo primero que puedes intentar sería esto:
```
sudo dpkg --configure -a
```

Si no te funciona:
```
sudo apt-get -f install
```

---

### Post by Diegox on 2010-01-07
> **adam814 said:**
> Lo primero que puedes intentar sería esto:
```
sudo dpkg --configure -a
```Si no te funciona:
```
sudo apt-get -f install
```

Gracias por responder, mira:

- Al poner en la consola "sudo dpkg --configure -a" salió esto:
[B]
diego@diego-desktop:~$ sudo dpkg --configure -a
[sudo] password for diego: 
dpkg: problemas de dependencias impiden la configuración de ttf-dejavu:
 ttf-dejavu depende de ttf-dejavu-extra; sin embargo:
 El paquete `ttf-dejavu-extra' no está configurado todavía.
dpkg: error al procesar ttf-dejavu (--configure):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 ttf-dejavu[/B]

Y al poner "sudo apt-get -f install" salió esto:

[B]diego@diego-desktop:~$ sudo apt-get -f install
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.
  libopenal1 wine-gecko postfix twolame mplayer-skins libsvga1 lsb-graphics
  libavidemux0 m4 amarok-common kdemultimedia-kio-plugins ncurses-term
  libkcddb4 libqtscript4-core avidemux-common libqtscript4-gui
  libqtscript4-uitools pax liblzo2-2 libqtscript4-sql libqtscript4-xml
  mjpegtools bsd-mailx libtag-extras1 mailx winbind liblastfm0 lsb-core lame
  alien amarok-utils libqtscript4-network lsb-cxx
Utilice «apt-get autoremove» para eliminarlos.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
2 no instalados del todo o eliminados.
Se utilizarán 0B de espacio de disco adicional después de esta operación.
Configurando ttf-dejavu-extra (2.29-2) ...
E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status.
dpkg: error al procesar ttf-dejavu-extra (--configure):
 el subproceso script post-installation instalado devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de ttf-dejavu:
 ttf-dejavu depende de ttf-dejavu-extra; sin embargo:
 El paquete `ttf-dejavu-extra' no está configurado todavía.
dpkg: error al procesar ttf-dejavu (--configure):
 problemas de dependencias - se deja sin configurar
No se ha escrito ningún informe de Apport porque el mensaje de error indica que es un error proveniente de un fallo anterior.
 Se encontraron errores al procesar:
 ttf-dejavu-extra
 ttf-dejavu
E: Sub-process /usr/bin/dpkg returned an error code (1)

[/B]Y continua apareciendo el mismo mensaje de error al instalar :(

---

### Post by adam814 on 2010-01-07
Bueno...¿Sale algo si pones "ps -e | grep defoma" en la consola?

Si no aparece ningún proceso "defoma" a lo mejor se resuelve la situación haciendo lo que pide con "sudo defoma-reconfigure -f" y despues "sudo apt-get -f install".

---

### Post by Diegox on 2010-01-07
Viendo la información posteada en otro post relacionado logré areglar el problema! Gracias a el que contestó :D

---

### Post by Diegox on 2010-01-07
> **adam814 said:**
> Bueno...¿Sale algo si pones "ps -e | grep defoma" en la consola?

Si no aparece ningún proceso "defoma" a lo mejor se resuelve la situación haciendo lo que pide con "sudo defoma-reconfigure -f" y despues "sudo apt-get -f install".

Usé un comando como ese recuerdo la frase "Grep", al final borré un archivo llamado "ttf.dejavu-extra.postinst" y despues apt-get -f install y listo.- Gracias por tu ayuda de todas maneras

---

