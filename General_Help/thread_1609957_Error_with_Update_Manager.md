---
title: "Error with Update Manager"
date: 2010-10-31
forum: General Help
---

### Post by Purpleandblue on 2010-10-31
Hey,

I just got this error message when Update Manager tried updating:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'sudo' is not known on line 56 in source list /etc/apt/sources.list'

I've been using Ubuntu for awhile, so I know my way around some stuff, but I'm completely lost on what to do here.

Thanks!

---

### Post by Quackers on 2010-10-31
If you go to Update Manager and click on settings, bottom left of the window, then go to Other Software tab, is there anything in there that includes "sudo"?

---

### Post by Purpleandblue on 2010-10-31
Can't do that.  As soon as I open Update Manager, I get that error click it off, and then Update Manager closes.  Anything else I can do?

---

### Post by Quackers on 2010-10-31
I don't know if it will be any more successful, but you could go into Synaptic and under the Settings menu select Repositories, then Other Software.

---

### Post by cpmman on 2010-10-31
Open terminal

```
sudo gedit /etc/apt/sources.list
```

edit as necessary the line containing "sudo" (carefully!)

save and exit

```
sudo apt-get update
```

---

