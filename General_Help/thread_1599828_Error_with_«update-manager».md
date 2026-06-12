---
title: "Error with «update-manager»"
date: 2010-10-18
forum: General Help
---

### Post by Iron Xalao on 2010-10-18
'E:Línea 61 mal formada en lista de fuentes /etc/apt/sources.list (análisis de URI)'

---

### Post by diablo75 on 2010-10-18
I don't speak Spanish but I think that says line 61 of your /etc/apt/sources.list file is "malformed".

Try the following.

Click Applications>Accessories>Terminal

Type:

```
gksudo gedit /etc/apt/sources.list
```

Comment out line 61 by adding a # to the beginning of the line.

#so it looks like this

This will cause Ubuntu to skip over that line, but it won't tell us why the line threw up a red flag in the first place.  To answer that question, copy and paste the file into this thread so others can examine it.


-----------spanish------------

Yo no hablo español, pero creo que dice la línea 61 del fichero / etc / apt / sources.list es "incorrecto".

Pruebe lo siguiente.

Haga clic en Aplicaciones> Accesorios> Terminal

Tipo:

```
gksudo gedit /etc/apt/sources.list
```

Comente la línea 61, añadiendo un # al principio de la línea.

# Por lo que se ve así

Esto hará que Ubuntu para saltar sobre esa línea, pero no nos dicen por qué la línea levantó una bandera roja en el primer lugar. Para responder a esa pregunta, copie y pegue el archivo en este hilo para que otros puedan examinarla.

---

### Post by Iron Xalao on 2010-10-18
:guitar:

You rock man, since i start using ubuntu this is the first time somebody help me, thanks a lot

---

