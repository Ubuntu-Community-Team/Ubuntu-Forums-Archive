---
title: "Ayuda creo q son problemas de permisos"
date: 2009-11-15
forum: General Help
---

### Post by Umanchuk on 2009-11-15
Bueno la cosa es que no puedo instalar programas soy nuevo usuario pero de repente dejo de funcionar me lanza un mensaje de error que dice 

se requiere autenticacion para instalar paquetes de software 

Una aplicacion esta intentamdo realizar una accion que necesita permisos especiales. Es necesario autentucarse para realizar dicha accion.

>Detalles

                                                           Cancelar    Autenticar

le doy autenticar no ac pero ni pio(nada) de igual forma desde usuarios y grupos tampoco puedo acceder pareciera que mi usuario haya perdido todos los permisos pero entre como root y este los posee todos no se que pasa no se si sera problema que haya cambiado los permisos a la carpeta USR le puse creo q 777 tambien puedo entrar por terminal como root pero ni idea tampoco que puedo hacer como dige soy nuevo...

---

### Post by fluffman86 on 2009-11-15
¿Ha intentado utilizar "sudo" antes de un nombre de programa? Por ejemplo:
```
sudo apt-get install mplayer
```
se instalará mplayer.

O si tiene que ejecutar fdisk, utilice:
```
sudo fdisk
```

---

### Post by Umanchuk on 2009-11-15
si el sudo despues de auteticarme en terminal funxiona normalmente pero para instalar por synaptic y/o centro de software ubuntu no funciona al igual que en la parte de usuarios y grupos que tampoco me deja autentiucarme dice fallo de autenticacion sin nisiquiera haber introducido contraseña alguna te dejo unas capturas por synaptic ni entra le doy y nunca abre la aplicacion


[[IMG]http://img402.imageshack.us/img402/5922/pantallazop.th.png[/IMG]]("http://img402.imageshack.us/i/pantallazop.png/")

[[IMG]http://img265.imageshack.us/img265/7677/pantallazo1a.th.png[/IMG]]("http://img265.imageshack.us/i/pantallazo1a.png/")


gracias de antemano

***************************************************************************************


Si quiero intalar algo abrir synaptip o cambiar o agregar grupos y/o usuarios tengo que iniciar sesión en el sistema como root cosa que no hacia antes no se que asa alguien me prodria ayudar se los agradeceria... T_T

---

### Post by Umanchuk on 2009-11-15
Otra cosa recueden porlomenos yo creo que viene el problema porque me meti con los permisos de la carpeta USR Ayuda xD


Ni siquiera el gksu [nautilus]("http://nautilus.softonic.com/linux") me lo deja ejecutar o porlomenos no aparece dice iniciando aplicacion administrativa pero puff desaparece

---

