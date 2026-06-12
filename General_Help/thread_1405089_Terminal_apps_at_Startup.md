---
title: "Terminal apps at Startup"
date: 2010-02-12
forum: General Help
---

### Post by Raff1 on 2010-02-12
Hello! I'm trying to run IRSSI at startup. I added the command "irssi" to System > Prefs > Startup Applications, but nothing happens. I guess I need a flag to make a terminal open (or stay open?), like "irrsi -flag".

Can anyone help me? And if you could tell me how to make it appear in a certain workspace as well, I would be very happy :)

---

### Post by wojox on 2010-02-12
In the Command part if the PATH is not set properly, click on Browse and choose the IRSSI executable.

---

### Post by nothingspecial on 2010-02-12
In the command box

```
gnome-terminal -x irrsi
```

---

### Post by Raff1 on 2010-02-12
> **nothingspecial said:**
> In the command box

```
gnome-terminal -x irrsi
```

It didn't work. I just got an error stating that something wrong happened with the child process.. This one worked pretty good btw:

```
gnome-terminal -x bash -c irssi
```

But moving it to another workspace is not that easy?

Thanks for the help :D

---

### Post by nothingspecial on 2010-02-12
> **Raff1 said:**
> It didn't work. I just got an error stating that something wrong happened with the child process.

It should work??????

Works for me, I just tested it.

Oh well, aslong as you got it going.

By the way, there is an app that lets you set rules for where apps open and such like, but I can`t for the life of me remember the name of it. If it comes to me.........

---

### Post by VCoolio on 2010-02-12
> **nothingspecial said:**
> 
By the way, there is an app that lets you set rules for where apps open and such like, but I can`t for the life of me remember the name of it. If it comes to me.........

That would be devilspie, or try the compiz place plugin if you use compiz.

---

### Post by nothingspecial on 2010-02-12
> **VCoolio said:**
> That would be devilspie, 

That`s the one :P

---

### Post by Raff1 on 2010-02-17
> **VCoolio said:**
> That would be devilspie, or try the compiz place plugin if you use compiz.

Ah thanks!  I will look into my compiz settings. Markin thread as solved as well.

---

