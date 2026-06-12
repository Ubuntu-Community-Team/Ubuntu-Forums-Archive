---
title: "Just can't solve this, please help"
date: 2011-08-27
forum: General Help
---

### Post by Lucifer_x_ on 2011-08-27
Hi! I was trying to install "badgerports" using this instrucctions [http://www.phaerus.com/?p=8](http://www.phaerus.com/?p=8) and well... I couldn't do it, I modified the "sources.list" and then everything wen't wrong, I tried then to use
> apt-get update
apt-get upgrade

soooo... The terminal did many things, and then gives me an error of "migrating" something n.nU... sorry I didnt pay much atention u.u...

so the "upgrade" never finished, then I restarted my PC returned the "sources.list" to it's original form, tried again the update and upgrade... and after a bunch of error that I "managed to solve" I'm stuck in this

> Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Los siguientes paquetes se han retenido:
  libstreamanalyzer0 libstreams0 plymouth python-cairo python-libxml2
  python-notify python-pycurl python-pygoocanvas python-rdflib
  xserver-xorg-video-cirrus
0 actualizados, 0 se instalarán, 0 para eliminar y 10 no actualizados.
4 no instalados del todo o eliminados.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? s
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Recurso no disponible temporalmente
Configurando sysv-rc (2.88dsf-13.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Recurso no disponible temporalmente
dpkg: error al procesar sysv-rc (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de initscripts:
 initscripts depende de sysv-rc | file-rc; sin embargo:
 El paquete `sysv-rc' no está configurado todavía.
  El paquete `file-rc' no está instalado.
dpkg: error al procesar initscripts (--configure):
 problemas de dependencias - se deja sin configurar
Configurando man-db (2.5.9-4) ...
No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
                                           debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Recurso no disponible temporalmente
dpkg: error al procesar man-db (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 1
Configurando update-inetd (4.38+nmu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Recurso no disponible temporalmente
dpkg: error al procesar update-inetd (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 1
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
         Se encontraron errores al procesar:
 sysv-rc
 initscripts
 man-db
 update-inetd
E: Sub-process /usr/bin/dpkg returned an error code (1)
lucifer@lucifer-Compaq-Presario-C700-Notebook-PC:~$ aptitud safe-upgrade
No se ha encontrado la orden «aptitud», quizás quiso decir:
 La orden «aptitude» del paquete «aptitude» (main)
 La orden «aptitude» del paquete «aptitude-gtk» (universe)
aptitud: orden no encontrada
lucifer@lucifer-Compaq-Presario-C700-Notebook-PC:~$ aptitude safe-upgrade
El programa «aptitude» puede encontrarse en los siguientes paquetes:
 * aptitude
 * aptitude-gtk
Pruebe: sudo apt-get install <paquete seleccionado>
lucifer@lucifer-Compaq-Presario-C700-Notebook-PC:~$ aptituede upgrade
No se ha encontrado la orden «aptituede», quizás quiso decir:
 La orden «aptitude» del paquete «aptitude» (main)
 La orden «aptitude» del paquete «aptitude-gtk» (universe)
aptituede: orden no encontrada
lucifer@lucifer-Compaq-Presario-C700-Notebook-PC:~$ sudo aptitude upgrade
sudo: aptitude: command not found
lucifer@lucifer-Compaq-Presario-C700-Notebook-PC:~$ sudo apt-get upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Los siguientes paquetes se han retenido:
  libstreamanalyzer0 libstreams0 plymouth python-cairo python-libxml2
  python-notify python-pycurl python-pygoocanvas python-rdflib
  xserver-xorg-video-cirrus
0 actualizados, 0 se instalarán, 0 para eliminar y 10 no actualizados.
4 no instalados del todo o eliminados.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? s
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Recurso no disponible temporalmente
Configurando sysv-rc (2.88dsf-13.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Recurso no disponible temporalmente
dpkg: error al procesar sysv-rc (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de initscripts:
 initscripts depende de sysv-rc | file-rc; sin embargo:
 El paquete `sysv-rc' no está configurado todavía.
  El paquete `file-rc' no está instalado.
dpkg: error al procesar initscripts (--configure):
 problemas de dependencias - se deja sin configurar
Configurando man-db (2.5.9-4) ...
No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
                                           debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Recurso no disponible temporalmente
dpkg: error al procesar man-db (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 1
Configurando update-inetd (4.38+nmu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Recurso no disponible temporalmente
dpkg: error al procesar update-inetd (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 1
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
         Se encontraron errores al procesar:
 sysv-rc
 initscripts
 man-db
 update-inetd


I can't upgrade or remove what I did wrong u.u...
plz help me to return this to it's original form!
If you need more info I'll be happy to give it

---

### Post by raja.genupula on 2011-08-27
[http://askubuntu.com/questions/15433/fixing-could-not-get-lock-var-lib-dpkg-lock](http://askubuntu.com/questions/15433/fixing-could-not-get-lock-var-lib-dpkg-lock)

---

### Post by Lucifer_x_ on 2011-08-27
I still can't sorry, I'm desperate
tried the first thing
> sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock

and it just killed my pc
Then restarted it and I tried again to upgrade

This were the results
After the message "trying to see if migration is safe" or something like that, the terminal comes with a purple bacground saying this:
> 
No se ha podido migrar al sistema de arranque basado en dependencias        
 &#9474;                                                                             
 &#9474; Las pruebas han determinado que existen los siguientes problemas en el      
 &#9474; sistema de arranque, que impiden la migración a la secuencia de arranque    
 &#9474; basada en dependencias:                                                     
 &#9474;                                                                             
 &#9474; package initscripts left obsolete init.d script behind, insserv:            
 &#9474; warning: script 'K20acpi-support' missing LSB tags and overrides,           
 &#9474; insserv: warning: script 'S49console-setup' missing LSB tags and            
 &#9474; overrides, insserv: warning: script 'rsyslog' missing LSB tags and          
 &#9474; overrides, insserv: warning: script 'udevmonitor' missing LSB tags and      
 &#9474; overrides, insserv: warning: script 'udev' missing LSB tags and             
 &#9474; overrides, insserv: warning: script 'cups' missing LSB tags and  
 | overrides, insserv: warning: script 'udev-fallback-graphics' missing LSB    
 &#9474; tags and overrides, insserv: warning: script 'plymouth-splash' missing      
 &#9474; LSB tags and overrides, insserv: warning: script 'plymouth-stop' missing
LSB tags and overrides, insserv: warning: script 'apport' missing LSB       
 &#9474; tags and overrides, insserv: warning: script 'cron' missing LSB tags and    
 &#9474; overrides, insserv: warning: script 'module-init-tools' missing LSB tags    
 &#9474; and overrides, insserv: warning: script 'acpi-support' missing LSB tags     
 &#9474; and overrides, insserv: warning: script 'plymouth-log' missing LSB tags     
 &#9474; and overrides, insserv: warning: script 'network-interface-security'        
 &#9474; missing LSB tags and overrides, insserv: warning: script 'avahi-daemon'     
 &#9474; missing LSB tags and overrides, insserv: warning: script 'udev-finish'      
 &#9474; missing LSB tags and overrides, insserv: warning: script 'hwclock'          
 &#9474; missing LSB tags and overrides, insserv: warning: script 'hostname'         
 &#9474; missing LSB tags and overrides, insserv: warning: script 'plymouth'         
 &#9474; missing LSB tags and overrides, insserv: warning: script 'console-setup'
missing LSB tags and overrides, insserv: warning: script 'procps'           
 &#9474; missing LSB tags and overrides, insserv: warning: script 'udevtrigger'      
 &#9474; missing LSB tags and overrides, insserv: warning: script 'hwclock-save'     
 &#9474; missing LSB tags and overrides, insserv: warning: script                    
 &#9474; 'plymouth-upstart-bridge' missing LSB tags and overrides, insserv:          
 &#9474; warning: script 'irqbalance' missing LSB tags and overrides, insserv:       
 &#9474; warning: script 'atd' missing LSB tags and overrides, insserv: warning:     
 &#9474; script 'anacron' missing LSB tags and overrides, insserv: warning:          
 &#9474; script 'alsa-store' missing LSB tags and overrides, insserv: warning:       
 &#9474; script 'network-interface' missing LSB tags and overrides, insserv:         
 &#9474; warning: script 'gdm' missing LSB tags and overrides, insserv: warning:     
 &#9474; script 'ufw' missing LSB tags and overrides, insserv: warning: script 
'dmesg' missing LSB tags and overrides, insserv: warning: script            
 &#9474; 'alsa-restore' missing LSB tags and overrides, insserv: warning: script     
 &#9474; 'acpid' missing LSB tags and overrides, insserv: warning: script            
 &#9474; 'network-manager' missing LSB tags and overrides, insserv: warning:         
 &#9474; script 'failsafe-x' missing LSB tags and overrides, insserv: warning:       
 &#9474; script 'dbus' missing LSB tags and overrides

I dont know what to do O.o, I'll try again with

---

### Post by snowpine on 2011-08-27
> **Lucifer_x_ said:**
> Hi! I was trying to install "badgerports" using this instrucctions [http://www.phaerus.com/?p=8](http://www.phaerus.com/?p=8) and well... I couldn't do it, I modified the "sources.list" and then everything wen't wrong

The instructions in your link are for Debian Lenny (the 2009 release). If you are using Debian Lenny then you'll find help here: [http://forums.debian.net](http://forums.debian.net)

If you are using Ubuntu then you have almost definitely broken your system by following these instructions. sources.list is an important system file that should only be edited if you know exactly what you're doing. Adding Debian Lenny sources to an Ubuntu install and then upgrading your system is very dangerous!

I recommend a fresh Ubuntu install and then find a reliable and trusted guide (such as UbuntuForums) to installing this application specifically for your Ubuntu release.

(sorry I don't really understand the Spanish but perhaps a bilingual forum member will notice something I've missed)

---

### Post by Lucifer_x_ on 2011-08-27
ooooh... now I get it u.u... damn

Can I "repair" the OS with a live-cd?

what I'm trying to do here is not to kill all my info/archives/aplications/etc

¿can I repair the OS without killing my info and archives? O.o

---

### Post by snowpine on 2011-08-27
> **Lucifer_x_ said:**
> ooooh... now I get it u.u... damn

Can I "repair" the OS with a live-cd?

what I'm trying to do here is not to kill all my info/archives/aplications/etc

¿can I repair the OS without killing my info and archives? O.o

I hope so!

But you should also make a backup of your info and archives to an external drive. This is always a smart idea. ;)

Good luck! :)

---

### Post by bruno9779 on 2011-08-27
You can backup all your personal data easily (it is all in the /home folder)
but you will need to reinstall all your applications.

In your place I would consider moving /home to it's own partition and reinstall specifying manually not to format /home.

PS: puedes probar con esta guia : [http://www.ubuntu-es.org/node/58233](http://www.ubuntu-es.org/node/58233)

---

### Post by Lucifer_x_ on 2011-08-27
Thank you all for the help! ^^
I'll repair the OS ASAP and I'll tell you how it comes

And well... the most important thing here was that I learned to only follow tutorials for ubuntu when I'm using ubuntu XD

^^

Gracias por la guia Bruno! la voy a probar ^^

Sorry XD, i got another question, I remember that there is somewhere a "list" of the aplicaions I have insalled, and I can copie the list via Terminal, I dont remember how O.o
do you know how? XD

---

### Post by bruno9779 on 2011-08-28
[http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)

You have issues just with that part of the OS, so it may not work.

---

