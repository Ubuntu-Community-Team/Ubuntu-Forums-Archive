---
title: "Apache2 no inicia"
date: 2011-09-07
forum: General Help
---

### Post by HTZANIMA3D on 2011-09-07
hola amigos,,pues tengo este problemita...instalo el apache2..y ahora no me inicia el servicio y en /etc/init.d/ no aparece apache2...lo he desinstalado e instalado varias veces..pero nada...
saludos...

---

### Post by Wim Sturkenboom on 2011-09-07
Can you repeat in english please?

google translate helps a bit ;)

Can you start the service with *_sudo service httpd start_*? I don't really use Ubuntu server, but seem to remember

---

### Post by HTZANIMA3D on 2011-09-07
Ups .. sorry ..i forget that friends .. 
The little problem is this: 
install  the apache2 .. and now I start the service and / etc / init.d / apache2  does not appear ... I have uninstalled uninstalled several times .. but  nothing ... 
greetings ...

---

### Post by HTZANIMA3D on 2011-09-07
when I put that command, this is what I said:
httpd: unrecognized service

---

### Post by Wim Sturkenboom on 2011-09-08
How did you install? From repositories?

And it should be *_sudo service apache2 start_* (my mistake). But if you state that it's not in /etc/init.d, I don't think it will work.

---

### Post by salemeni on 2011-09-08
```


sudo /etc/init.d/apache2 status

```
to check the status of apache service.
If is running like this
```


Apache2 is running (pid 3714).

```
Test with browser 
[http://127.0.0.1](http://127.0.0.1)

---

