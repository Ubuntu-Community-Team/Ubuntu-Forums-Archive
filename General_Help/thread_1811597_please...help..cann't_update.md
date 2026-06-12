---
title: "please...help..cann't update"
date: 2011-07-25
forum: General Help
---

### Post by hhadisi on 2011-07-25
i have installed granola with .bash and when it finished installation, then i try to update my ubuntu, but myupdate manager cann't run and show warning like this :

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 1 in source list /etc/apt/sources.list.d/miserware.list (dist parse)'

..can anyone help me how to fix this error.
Pleaseeee....

---

### Post by plucky on 2011-07-25
> 'E:Malformed line 1 in source list /etc/apt/sources.list.d/miserware.list (dist parse)'


Open a terminal and ```
gksudo gedit /etc/apt/sources.list.d/miserware.list
``` and  post the output.

---

### Post by hhadisi on 2011-07-25
this is the output gksudo gedit /etc/apt/sources.list.d/miserware.list :

deb [https://download.miserware.com/linux/deb](https://download.miserware.com/linux/deb)  

and what should i do with the output?

---

### Post by plucky on 2011-07-25
> **hhadisi said:**
> this is the output gksudo gedit /etc/apt/sources.list.d/miserware.list :

deb [https://download.miserware.com/linux/deb](https://download.miserware.com/linux/deb)  

and what should i do with the output?

Just installed it and this is what is in my file ```
deb https://download.miserware.com/linux/deb natty main
```

I am running natty,if you are running another version you will have to change natty to <whatever version> you are using.

Good Luck

---

### Post by hhadisi on 2011-07-25
horaiii.....you're briliant.....thank's very much...

---

