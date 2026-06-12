---
title: "Error -  Group: cannot find name for group ID 0"
date: 2010-04-17
forum: General Help
---

### Post by ez-rmk on 2010-04-17
Buenas gente... soy nuevo en linux y me salto este error...

[FONT=courier new]Mount  of filesystem failed.
A maintenance shell will now be started
CONTROL-D  will terminate this shell and retry.
groups: cannot find name for group ID 0
root@Sergioc-desktop:"#[/FONT]

que puedo hacer :( ? porq no inicia...

---

### Post by quixote on 2010-04-19
Hm- my Spanish is none too good, so I can't answer your question properly.  It sounds like your system has lost its connection to the root account, which can only be fixed using "visudo".  But if your system won't boot at all, I'm not sure how you'd go about starting it up to fix that.

Hopefully, somebody who speaks Spanish and knows all about visudo and no "group ID 0" will jump in! :D

---

### Post by darolu on 2010-04-19
Hola, como quixote dijo, tu sistema ha perdido la conexión con la cuenta root; el grupo con identificación 0 es el grupo root, cosas como estas pasan cuando entras como root a tu sistema, por eso hay que usar sudo para labores administrativas.

Parece ser que puedes entrar a tu computadora, aunque sea en modo de comando de línea, desde allí puedes ejecutar "visudo" y agregar nuevamente el grupo root.

Otra cosa que puedes intentar, es ir a Sistema - Administración - Usuarios y grupos y después de poner tu password, dar click en 'gestionar grupos'; uno de los grupos debe aparecer en blanco (solo un espacio) ahí lo editas, te aseguras de que sea el grupo "0" y le pones por nombre "root", si no existe, creas el grupo.

---

