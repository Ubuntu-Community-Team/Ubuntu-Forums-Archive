---
title: "Problema al entrar a Ubuntu..."
date: 2009-09-28
forum: General Help
---

### Post by Ðickinson!® on 2009-09-28
Hola comunidad, se me presento el siguiente problema, en el menu al iniciar aplico el kernel actual y me da el siguiente error:

```
[0.309769]ACPI : Aborted because bad gzip magic numbers
[3.054338]Kernel Panic - not syncing : VFS : Unable to mount root fs on unknown-block (0,0)
```Entre con el modo de rescate, empese a ver por internet y salia que debia poner en el terminal lo siguiente:

```
update-initramfs -k all -c -v
```y de ahi deberia reiniciar sin preocupaciones, pero el problema es que no me funciona ya que pongo ese comando en la concola sale que agrega hartas cosas pero al final me sale el siguiente problema:

```
Building cpio /boot/initrd.img-2.6.28-11-generic.new initramfs
/usr/sbin/mkinitramfs: 323: cannot create /boot/initrd.img-2.6.28-11-generic.new: Permission denied
update-initramfs: failed for /boot/initrd.img-2.6.28-11-generic
```creo que no me deja aplicar esos cambios que segun dicen en internet me solucionaria el problema, queria saber si alguien de ustedes sabe acerca de esto y me podria ayudar please que lo necesito urgente, eso seria sl2 y gracias de antemano

PD: sorry por postear en español, me meti pensando que era comunidad chilena....

---

### Post by Zill on 2009-09-28
Sorry, but this forum uses English.  This site may help...

[http://www.ubuntu-es.org/index.php?q=forum]("http://www.ubuntu-es.org/index.php?q=forum")

---

