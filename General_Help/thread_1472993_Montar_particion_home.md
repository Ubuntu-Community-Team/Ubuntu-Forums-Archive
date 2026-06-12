---
title: "Montar particion /home"
date: 2010-05-04
forum: General Help
---

### Post by Sleipnirnkn on 2010-05-04
Estimados: Tengo una consulta,

Para que entiendan la situacion:
Actualice de Karmic a Lucid, y tuve varios inconvenientes (lease GRUB, Drivers ATI, Wireless, etc) todos solucionables. Mi nuevo ubuntu 10.04 no estaba funcionando como esperaba y me molesta bastante no tener todo ordenado,hasta los mas minimos detalles, por lo que opté por re-instalar haciendo una instalacion limpia de Ubuntu 10.04.

Las Particiones de mi disco son asi: (Antes de la re-instalacion limpia de ubuntu 10.04):

/dev/sda1  20GB  ntfs  (Para Windows)
/dev/sda2  30GB  ext4  Ubuntu / (root)
/dev/sda5  1GB   Swap  -
/dev/sda6  100GB ext4  /home

 
Después de esto, bajé la ISO de ubuntu, la grabé en un pen, e instalé nuevamente, pero esta vez seleccioné lo siguiente.

/dev/sda2  30GB  ext4 Ubuntu (root)  y marcada para formatear.
y
/dev/sda5 para swap 

NOTA: No seleccioné aca mi anterior particion sda6 para ser /home (Es acá donde creo que le erré).

Moraleja:
Actualmente tengo la Ubuntu 10.04 instalado limpio, una particion /home con data de Karmic y varios de mis archivos en ella.

Mi pregunta es la siguiente:
1) Puedo de alguna manera, apuntar mi actual carpeta /home a la particion /home ?

2) En el caso que fuera posible, la vieja configuracion que esta en la particion /home que pertenece a Karmic, afectaria el funcionamiento de Lucid o sus programas ?

Desde ya, espero haber sido claro, y ojala puedan darme una mano para aclarar mis dudas.

---

### Post by Sleipnirnkn on 2010-05-04
Despues de googlear un poco encontré la solucion en el link de abajo y ya está en práctica, de todos modos, gracias.
Seguramente la solución le servirá a otros. 

[http://www.ubuntu-es.org/index.php?q=node/58233](http://www.ubuntu-es.org/index.php?q=node/58233)

---

