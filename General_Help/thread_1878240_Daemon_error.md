---
title: "Daemon error?"
date: 2011-11-09
forum: General Help
---

### Post by archibold9 on 2011-11-09
Hi. I'm running ubuntu 11.10 and i get this error when trying to install something from ubuntu software centre 'There seems to be a programming error in aptdaemon. This is the software that allows you to install/remove software and to perform other package management related tasks.' 
>Details
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

This means i can't download anything D:.
Help please!:(

---

### Post by archibold9 on 2011-11-09
Bump :'( Sorry but i'm desperate :p

---

### Post by Benetosh on 2012-05-22
Seguro ya lo resolviste pero para futuras referencias solo necesitas ejecutar en una termial lo siguiente:

  sudo apt-get install -f

y tal vez también tengas que ejecutar la siguiente linea si el sistema te lo pide

  sudo dpkg --configure -a

Así corregí este problema y todo quedo bien.

* Starting the Winbind daemon winbind                                   [ OK ] 

Saludos

---

