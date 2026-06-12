---
title: "nautilus crashes when i open &quot;computer&quot; or trash"
date: 2009-07-06
forum: General Help
---

### Post by chriskin on 2009-07-06
opening the "computer" -at places for example- gives me a second of the folder and then it crashes

same thing happens with the trash

:popcorn:
[B]
EDIT : SOLVED [/B], see post no.4

---

### Post by chriskin on 2009-07-06
opening with terminal gives me 

```
Initializing nautilus-open-terminal extension
Initializing nautilus-dropbox 0.6.1
Initializing nautilus-image-converter extension
** Message: Initializing gksu extension...

** (nautilus:8490): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```

and when i open the computer after that i get a seg fault 

```

Segmentation fault

```

---

### Post by chriskin on 2009-07-06
does anyone know ?

i installed samba and now the error changes to this one
```
Initializing nautilus-open-terminal extension
Initializing nautilus-dropbox 0.6.1
Initializing nautilus-image-converter extension
** Message: Initializing gksu extension...

** (nautilus:30364): WARNING **: Unable to add monitor: Not supported
Segmentation fault
christos@CNB:~$
```

---

### Post by chriskin on 2009-07-06
in case anyone cares, it is an ubuntuone client bug, just upgrade it to the last version and you will be ok

I found it on some bug report :)

---

### Post by beforefirstlight on 2009-07-08
I have exactly the same problem. And I have just installed UbuntuOne !!
For me an upgrade doesn't solve the problem. An uninstall, unfortunately solved the problem.

---

### Post by chriskin on 2009-07-08
it started happening to me again even after the upgrade, it just stopped for a day or so

i only see one solution, i will remove ubuntu one

i can't say that it is worth the trouble anyway

---

