---
title: "Nautilus: need help with permissions"
date: 2010-08-02
forum: General Help
---

### Post by Keypel on 2010-08-02
I tired of having to open a shell to sudo this and sudo that when I want is to be able to drag n drop files and folders in Nautilus.

Most importantly, how do I get permission in Nautilus to do these things?


Also as a suggestion, wouldn't.t it be better if Nautilus just prompted you for a password instead of denying you permission?

---

### Post by Smart Viking on 2010-08-02
Hi, you do that by using gksudo, with the following command:

```
gksudo nautilus
```

Hope this helps, you could create a launcher on the desktop with that command, and it would prompt you for a password when you double-click it. :)

---

### Post by Keypel on 2010-08-02
Thanks that worked. 

I'll have to remember gksudo nautilus. But what does gksudo stand for? I mean when you type gksudo nautilus what exactly is happening? ie is nautilus the program and gksudo is the option? why not just sudo nautilus? If I understood what was happening under the hood it would help me remember the commands and maybe I wouldn't hate the commands. Is there a book or something I should be reading?

---

### Post by JustinR on 2010-08-02
> **Keypel said:**
> Thanks that worked. 

I'll have to remember gksudo nautilus. But what does gksudo stand for? I mean when you type gksudo nautilus what exactly is happening? ie is nautilus the program and gksudo is the option? why not just sudo nautilus? If I understood what was happening under the hood it would help me remember the commands and maybe I wouldn't hate the commands. Is there a book or something I should be reading?

GKSUDO is a command thats sudo - but meant for graphical applications. Permissions sometimes are confused with Ubuntu if you use sudo instead of gksudo with graphical applications.

---

