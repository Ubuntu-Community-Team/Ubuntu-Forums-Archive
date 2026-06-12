---
title: "$path"
date: 2010-10-24
forum: General Help
---

### Post by cucuru on 2010-10-24
Hello, I have a really strange problem...

I modify /etc/environment in order to add a new one.

this is what I have

```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"


```I modified it:

```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:
/usr/src/ns-allinone-2.31/ns-2.31"

```Saved the file, restarted my session and:

```

rocio@rocio-laptop:~$ $PATH
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:
/usr/src/ns-allinone-2.31/ns-2.31:/usr/src/ns-allinone-2.31/bin:/usr/src/ns-allinone-2.31/
tcl8.4.14/unix:/usr/src/ns-allinone-2.31/tk8.4.14/unix:/usr/src/ns-allinone-2.31/ns-2.31/
:/usr/src/ns-allinone-2.31/nam-1.13/: No existe el fichero ó directorio


```"No existe el fichero o directorio" means "the file or folder doesn't exist"

where is my problem?

thank you so much!!

---

### Post by amauk on 2010-10-24
You don't have a problem with your $PATH
Only in the way you've tested the new entry

Instead of```
user@machine:~$ $PATH
```
Do```
user@machine:~$ echo $PATH
```

Just $PATH in it's own will substitute the entire string (colon separated) to the shell, which will try to resolve the path
The path does not exist, hence the error

---

### Post by cucuru on 2010-10-24
ohhh it was so easy! I was wasting my time looking for my mistake!

Thank you so much!

---

### Post by amauk on 2010-10-24
no problem

---

