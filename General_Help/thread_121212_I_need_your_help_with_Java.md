---
title: "I need your help with Java"
date: 2006-01-24
forum: General Help
---

### Post by jrios_03 on 2006-01-24
Hi again...

I have a problem with the fakerrot in Ubuntu 5.04 and 5.10:
```
root@Kubuntu:~/Desktop# chmod -x jdk-1_5_0_05-linux-i586.bin 
root@Kubuntu:~/Desktop# fakeroot make-jpkg jdk-1_5_0_05_-linux-i586.bin 
fakeroot: preload library not found, aborting.

And when I execute this:
root@Kubuntu:~/Desktop# sudo apt-get install java-package fakeroot 
Leyendo lista de paquetes... Hecho 
Creando árbol de dependencias... Hecho 
E: No se pudo encontrar el paquete java-package

```
I need your help please...

---

### Post by az on 2006-01-24
java-package is in the multiverse repo, I think.

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

