---
title: "imposible to conect to cl.archive.ubuntu.com"
date: 2010-07-29
forum: General Help
---

### Post by Mago Jose on 2010-07-29
Every time i try to actualize my lucid lynx it sends me an error:

$ sudo apt-get dist-upgrade
Err [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-image-2.6.32-24-generic 2.6.32-24.38
  Imposible conectar a cl.archive.ubuntu.com:http:

and my friends are having the same problem.. .any ideas?
PD: also happens when I try to install something

ahora en español:

cada vez que intento actulizar el sistema, ya sea por el gestor de actualizaciones o por terminal me manda el mismo error:

$sudo apt-get dist-upgrade
Err [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-image-2.6.32-24-generic 2.6.32-24.38
  Imposible conectar a cl.archive.ubuntu.com:http:

mis amigos tienen el mismo error tambien. ademas tambien sucede cuando intento instalar algo... alguna idea...

Muchas gracias .

---

### Post by davidmohammed on 2010-07-29
sounds like your local repository is offline.

Suggest go to administration - software sources.  In the drop-down you see, click Other and choose a different repository location.

---

### Post by Mago Jose on 2010-07-29
okey, will do... thanks a lot

---

