---
title: "Booteo desde cd ubuntu 8.04 en hp"
date: 2009-08-18
forum: General Help
---

### Post by Mauricio Gardella on 2009-08-18
[SIZE=2]Soy nuevo con este S.O. y me dijeron que es muy potente por lo que he decidido comenzar a hacer las primeras experiencias. El problema que tengo es que al intentar bootear desde el CD me sale el siguiente mensaje y ahi quedo parado. [/SIZE]
 
 
[FONT=Arial][SIZE=2]udevd-event [1611] run-program: /sbin/modprobe. abnormal exit[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]Busybox v1.1.3 (debian 1:1.1.3 - 5ubuntu12)[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]Built-in shell (ash)[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]Enter 'help' for alist of buil-in comands[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]La PC es una HP PAVILION DV4 1425 que vino con Vista Preinstalado y estoy queriendo correr un UBUNTU 8.04 LTS[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]Si alguien me pudiera guiar como para saltear este problemita se lo agradecerpia mucho, este mismo CD con una PC anterior funciono.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]Muchas Gracias[/SIZE][/FONT]

---

### Post by seventyeights on 2009-08-18
Por favor, inténtelo de este.

ir a la BIOS y apagar la floppy.

O...

en el menú de inicio, pulse F6 y añadir a la final después de la "--":
all_generic_ide floppy=off irqpol

---

