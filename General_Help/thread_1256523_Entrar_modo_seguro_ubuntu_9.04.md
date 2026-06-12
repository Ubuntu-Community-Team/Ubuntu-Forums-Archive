---
title: "Entrar modo seguro ubuntu 9.04"
date: 2009-09-02
forum: General Help
---

### Post by martin1717 on 2009-09-02
alguien sabe como se entra al modo seguro en ubuntu jaunty? necesito saber esto con urgencia porq tengo q desinstalar un controlador de video q no me deja ver mi escritorio, ni siquiera loguearme. Gracias

---

### Post by rbc on 2009-09-02
Sorry. It’s been a long time since university Spanish class, so all this will be in English. Are you looking for Recovery Mode? If so, boot to grub. If you dual boot, it should be the second option in the list. If you have only Ubuntu, and grub is hidden, hit the Escape key and choose Recovery Mode from there.

---

### Post by martin1717 on 2009-09-02
Gracias por contestar. vamos a tener q hablar con traductor mediante porque tengo menos inlges que hugo chavez. dos preguntas: hay algun modo seguro grafico? y en caso de que no se pueda iniciar en modo grafico, como hago para desinstalar el xorg (controlador que instale y causo el problema) ?Gracias

---

### Post by fluffman86 on 2009-09-02
Usted no desea desinstalar Xorg. Eso es lo que todos los programas gráficos se ejecutan sobre. ¿qué tipo de tarjeta de video tiene?

---

### Post by martin1717 on 2009-09-02
tengo una ati radeon xpress 200m. el problema surgio despues de instalar un controlador libre para esta tarjeta desde los repositorios oficiales. lo ultimo q quiero hacer es reisntalar ubuntu porq pierdo todo. no hay alguna forma de deshacer esa instalacion? gracias

---

### Post by martin1717 on 2009-09-02
aca encontre la solucion: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
me di cuenta de q es fundamental saber usar la terminal, por los defectos logicos q tiene el modo grafico

---

### Post by fluffman86 on 2009-09-02
¿La página Web que encontró trabajo? ¿Está su equipo bien ahora?

---

