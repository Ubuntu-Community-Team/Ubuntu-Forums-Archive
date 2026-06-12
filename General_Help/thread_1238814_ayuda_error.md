---
title: "ayuda error"
date: 2009-08-12
forum: General Help
---

### Post by nacan on 2009-08-12
bueno soy nuevo en este foro y en linux ubuntu y hoy me aparesio este error: dejo fotos:
muchas gracias y espero respuestas ;)

[http://img39.imageshack.us/img39/2120/errorfgp.png](http://img39.imageshack.us/img39/2120/errorfgp.png)

[http://img140.imageshack.us/img140/994/error2l.png](http://img140.imageshack.us/img140/994/error2l.png)

[http://img30.imageshack.us/img30/9775/error3s.png](http://img30.imageshack.us/img30/9775/error3s.png)

---

### Post by pizza-is-good on 2009-08-12
puedes poner las fotos como attachments? Yo no las puedo ver cunado estan en el texto...

---

### Post by nacan on 2009-08-12
> **pizza-is-good said:**
> puedes poner las fotos como attachments? Yo no las puedo ver cunado estan en el texto...

listo ;)


[http://img39.imageshack.us/img39/2120/errorfgp.png](http://img39.imageshack.us/img39/2120/errorfgp.png)

[http://img140.imageshack.us/img140/994/error2l.png](http://img140.imageshack.us/img140/994/error2l.png)

[http://img30.imageshack.us/img30/9775/error3s.png](http://img30.imageshack.us/img30/9775/error3s.png)

---

### Post by Jesus_Valdez on 2009-08-12
Por que no haces eso que dice ahi? 

Abre la terminal, esta en Aplicaciones / Accesorios / Terminal

Y escribes sudo apt-get update Te va a pedir la contraseña, se la escribes, no te preocupes si no ves asteriscos ni nada, solo escribes la contraseña y le das a enter.

Y pues ya de ahi veremos que error te da, es el concejo que te puedo dar

EDITO, Añado imagen como attachment

---

### Post by nacan on 2009-08-13
> **Jesus_Valdez said:**
> Por que no haces eso que dice ahi? 

Abre la terminal, esta en Aplicaciones / Accesorios / Terminal

Y escribes sudo apt-get update Te va a pedir la contraseña, se la escribes, no te preocupes si no ves asteriscos ni nada, solo escribes la contraseña y le das a enter.

Y pues ya de ahi veremos que error te da, es el concejo que te puedo dar

EDITO, Añado imagen como attachment

pongo apt-get en consola y me aparese todo esto:


marco@marco-desktop:~$ apt-get
apt 0.7.20.2ubuntu6 para i386 compilado en Apr 17 2009 04:25:29
Uso: apt-get [opciones] orden
       apt-get [opciones] install|remove pkg1 [pkg2 ...]
       apt-get [opciones] source pkg1 [pkg2 ...]

apt-get es una sencilla interfaz de línea de órdenes para descargar e
instalar paquetes. Los comandos más frecuentemente usados son update
e install.

Comandos:
   update - Actualizar la lista de paquetes
   upgrade - Realizar una actualización
   install - Instalar nuevos paquetes (libc6 es un paquete, no libc6.deb)
   remove - Desinstalar paquetes
   autoremove - Desinstalar automáticamente paquetes en desuso
   purge - Desinstalar paquetes y sus archivos de configuración
   source - Descargar las fuentes de paquetes
   build-dep - Configurar la dependencias de generación de paquetes fuente
   dist-upgrade - Actualizar la distribución, ver apt-get(8)
   dselect-upgrade - Seguir las selecciones de dselect
   clean - Borrar los archivos descargados
   autoclean - Borrar los antiguos archivos descargados
   check - Comprobar que no existen dependencias incumplidas

Opciones:
  -h  Este texto de ayuda.
  -q  Salida para registros - sin indicador de progreso
  -qq Sin salida salvo que haya errores
  -d  Sólo descargar - No se instalan ni desempaquetan archivos
  -s  No actúa. Realiza una simulación
  -y  Asume como Sí la respuesta a todas las preguntas y no pregunta nada
  -f  Intenta corregir un sistema las dependencias incumplidas
  -m  Intenta continuar aunque haya archivos ilocalizables
  -u  Muestra también la lista de paquetes actualizados
  -b  Construye el paquete fuente después de descargarlo
  -V  Muestra los números de versión en la forma extendida
  -c=? Leer este archivo de configuración
  -o=? Establecer alguna opción de configuración, ej. -o dir::cache=/tmp
Ver las páginas del manual de apt-get(8), sources.list(5) y apt.conf(5)
para más información y opciones.
                       Este APT tiene poderes de super vaca.

---

### Post by nacan on 2009-08-14
alguien que me ayude porfa... no puedo ni instalar nada, ni bajas nada ni nada :S xD

---

### Post by jocampo on 2009-08-14
Trata lo siguiente (en ese orden)

```
sudo apt-get check
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

por cierto, desde que instalaste el sistema, jamas has podido bajar updates? suena como a que tu source list, esta roto o tiene entradas incorrectas

---

### Post by nacan on 2009-08-14
> **jocampo said:**
> Trata lo siguiente (en ese orden)

```
sudo apt-get check
``````
sudo apt-get update
``````
sudo apt-get upgrade
```por cierto, desde que instalaste el sistema, jamas has podido bajar updates? suena como a que tu source list, esta roto o tiene entradas incorrectas

sisi antes me andaba exelente todo para mi es el source list que algo me abre tocado agregandole un par de paguinas descargando cosas no se para mi es eso me podras pasar algun source list para ubuntu 9.0.4 ?

---

