---
title: "irssi cannot load any scripts! :-s"
date: 2009-08-30
forum: General Help
---

### Post by antdgar on 2009-08-30
I was using some scripts earlier. At that time I was root.
I closed irssi terminal and opened it again. I try to load any of my scripts:
```
/load script /home/antd/scc1.2.pl
``````
error loading module script /home/antd/scc1.2.pl
home/antd/scc1.2.pl_script: cannot open shared object file: No such file or directory
```Obviously it is in that directory. It was working moments earlier. Well, I cannot load ANY of my scripts no matter of there location. :confused:

Any ideas?

---

### Post by Liolikas on 2009-08-30
Script version is too old (became too old after system update fails to find things on which it depends). You should download new from where you downloaded old.

---

### Post by antdgar on 2009-08-30
> **Liolikas said:**
> Script version is too old (became too old after system update fails to find things on which it depends). You should download new from where you downloaded old.
The script is too old? It was working 10 mins ago. And this is an up-to-date script.

---

### Post by Liolikas on 2009-08-30
But you updated system in those 10 mins right?

Basically you have to contact script devs with thease questions. They can edit cript itself to fix things.

Or just learn Perl :guitar:

---

### Post by antdgar on 2009-08-30
I didn't update! But now I am reinstalling and definitely won't update (just in case i did by accident)

---

### Post by Liolikas on 2009-08-30
...? They can not just stop working because of moon faze change.

---

### Post by antdgar on 2009-08-30
We shall see once the reinstall of the OS is complete. I won't run updates.

edit: I ran updates BEFORE and it worked... then it stopped working. So it is the moon phase.

---

### Post by andrew.46 on 2009-09-01
Hi antdgar,

> **antdgar said:**
> I was using some scripts earlier. At that time I was root. I closed irssi terminal and opened it again. I try to load any of my scripts:
```
/load script /home/antd/scc1.2.pl
``````
error loading module script /home/antd/scc1.2.pl
home/antd/scc1.2.pl_script: cannot open shared object file: No such file or directory
```Obviously it is in that directory. 

I wonder if their is a file permision/ownership problem there. Could you run:

```
ls -l /home/antd/scc1.2.pl
```

and hopefully this might shed some light.

All the best,

Andrew

---

