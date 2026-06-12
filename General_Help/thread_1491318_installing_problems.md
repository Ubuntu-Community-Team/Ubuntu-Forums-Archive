---
title: "installing problems"
date: 2010-05-23
forum: General Help
---

### Post by leonela.fulgencio on 2010-05-23
Hi , im trying to install java  jdk and jre , but  al things i try to install i get this message. what can i do



E: Línea 49 mal formada en lista de fuentes /etc/apt/sources.list (análisis de dist)
E: No se pudieron leer las listas de fuentes.

---

### Post by TeoBigusGeekus on 2010-05-23
It would help us if you could translate it in English...

---

### Post by howefield on 2010-05-23
Open a terminal and type

```
gksudo gedit /etc/apt/sources.list
```

and remove or fix line 49.

Sun java is in the partner repository, enable it via Synaptic Package Manager and install that way.

---

### Post by cbecker78 on 2010-05-23
your sources list file (/etc/apt/sources.list) there is something wrong with the string on line 49...  run "gedit /etc/apt/sources.list" and and copy and paste the file text (between code tags) here.  someone should be able to help you straighten it out.  Most typically there is an extra space somewhere.

---

### Post by leonela.fulgencio on 2010-05-24
Hi , 
Thanks  for  your help it work , this is the best forum i ever try , your responses are trueeee:P

---

