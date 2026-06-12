---
title: "Ayuda!! Ubuntu Lucid no bootea, dice press s to skip mounting or m for manual recover"
date: 2010-10-13
forum: General Help
---

### Post by ndelvalle on 2010-10-13
Ayuda!! Ubuntu Lucid no bootea, dice press s to skip mounting or m for manual recover, no se que hacer , agradecere su ayuda.
Googleando un poco encontre esto:
Bueno ahora averigua el uuid de la particion:

> sudo blkid /dev/sda5
copia el numero de uuid
Desp 
sudo gedit /etc/fstab
y reempazas sda5 por UUID=El numero que te dio
pero no entiendo, no sesi tendre que hacerlo diferente, aqui esta lo que me salio:
[IMG]http://img408.imageshack.us/img408/8783/sinnombred.jpg[/IMG]

---

