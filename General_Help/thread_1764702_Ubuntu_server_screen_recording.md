---
title: "Ubuntu server screen recording"
date: 2011-05-22
forum: General Help
---

### Post by Jragon on 2011-05-22
Hi!

Does anyone know how I could do some screen recording of Ubuntu server? I make tutorials and people have been asking me to do ubuntu servers stuff... What should I use/do?

Thanks

-Jragon

---

### Post by lmarmisa on 2011-05-22
You could try to use a remote computer running Ubuntu Desktop. Open a terminal in this computer and connect to the server using ssh:

```

ssh user@ubuntuserver

```

Finally record the session of your terminal using **recordmydesktop** or any other equivalent tool.

---

### Post by nothingspecial on 2011-05-22
Type

```
script -t 2> timingfile
```

Do your groovy terminal stuff, then type ```
exit
```

To view your groovy terminal stuff again type

```
scriptreplay timingfile
```

see 

```
man script
man script replay
```

To clarify after typing script, the first argument is the timing file and you can specify the output file also

so you can type 

```
script -t 2> bananas cheese
```

The record of your session is the file cheese and to replay it, you type ```
scriptreplay bananas
```

So, if you are going to do alot of this, I would suggest making a script directory and then a subdirectory for each script file and and timing file so you know what is what.

---

