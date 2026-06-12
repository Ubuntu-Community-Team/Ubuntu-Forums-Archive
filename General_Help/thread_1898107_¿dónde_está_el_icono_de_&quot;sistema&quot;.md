---
title: "¿dónde está el icono de &quot;sistema&quot;?"
date: 2011-12-20
forum: General Help
---

### Post by anersan on 2011-12-20
Hola,

Acabo de instalar Ubuntu 11.10 y soy el perfecto novato.
Me gustaría acceder a "Sistema" y luego "Administración" para configurar algunas cosillas que he visto en el foro, pero no encuentro esta opción por ninguna parte.

He probado con Ctrl + Alt + T y después he escrito "apt-get install bum" (sin las comillas). En alguna parte he leído que lo podría resolver así.
Pero me aparece esto:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Alguna sugerencia?

Gracias por la ayuda

---

### Post by zodrac on 2012-01-28
Hola. Veras, para poder hacer eso tienes que tener privilegios de root, lo que viene a ser administrador en windows. Lo único que tienes que hacer es ejecutar el comando tal y como te han dicho pero anteponiendo el comando "sudo". Algo así: "sudo apt-get install bum" y te pedirá tu contraseña.


Saludos.

---

