---
title: "Missing all files after GParted: please help urgent"
date: 2010-01-01
forum: General Help
---

### Post by jcangas on 2010-01-01
[SIZE=2]I'm using Ubuntu 9.10 AMD/64. I moved my data partition with GParted, resulting this message from GParted

[/SIZE][SIZE=2] ... ( omiting all previous reported ok,  gparted end of message: )
[/SIZE][SIZE=2]copiar 65536 sectores usando un tamaño de bloque de 65536 sectores  00:00:02    ( ÉXITO ) [/SIZE]        [SIZE=2]*65536 de 65536 copiados*[/SIZE]       [SIZE=2]*1.43313 segundos*[/SIZE]         [SIZE=2] El tamaño de bloque óptimo es 65536 sectores (32.00 MiB) 
[/SIZE][SIZE=2]copiar 445291699 sectores usando un tamaño de bloque de 65536 sectores  03:32:51    ( ÉXITO ) [/SIZE]        [SIZE=2]*445291699 de 445291699 copiados*[/SIZE]         [SIZE=2] 446012595 sectores copiados [/SIZE]           [SIZE=2] comprobar errores en el sistema de archivos en /dev/sda3 y (si es posible) arreglarlos  00:00:01    ( ERROR ) [/SIZE]        [SIZE=2]***e2fsck -f -y -v /dev/sda3***[/SIZE]         [SIZE=2][I]
El superbloque podría no ser leido o no describe un sistema de ficheros ext2 correcto.
Si el dispositivo es válido y en verdad contiene un sistema de ficheros ext2 (y no uno 
de intercambio, ufs o algo más), entonces el superbloque está corrompido
y podría intentarse ejecutar el e2fsck con un superbloque alternativo:
   e2fsck -b 8193 <dispositivo>

[/I][/SIZE]       [SIZE=2][I]e2fsck 1.41.9 (22-Aug-2009)
e2fsck: No existe el fichero ó directorio mientras se intentaba abrir /dev/sda3 
[/I][/SIZE]            [SIZE=2] mensajes de libparted    ( INFO ) [/SIZE]        [SIZE=2]*Error al informar el núcleo sobre las modificaciones en la partición /dev/sda3 -- Dispositivo ó recurso ocupado. Esto significa que Linux no reconocerá ningún cambio que haya hecho en /dev/sda3 hasta que lo reinicie -- por lo tanto no puede montarla o utilizarla antes de reiniciarla.*[/SIZE]       [SIZE=2]*El núcleo no pudo releer la tabla de particiones en /dev/sda (Dispositivo ó recurso ocupado). Esto significa que Linux no reconocerá las modificaciones que hizo. Debe reiniciarlo antes de hacer cualquier uso con /dev/sda.*[/SIZE]
Then I reboot from CD, and do e2fsck -n -f, this reports all ok, but I cannot see my files: I can view all folders, but they appear empty!!

Please, please can I retrieve my files??? the partition seems moved ok, so my data must be here isn't?

---

### Post by jcangas on 2010-01-01
:confused::confused::confused: ... finally I reboot from my HD (NOT CD), open nautilus one more time and .. voilà .. now my files are here !!!. Yes now the folders aren't empty  I dont understand what happens ...
well thanks anyway

---

