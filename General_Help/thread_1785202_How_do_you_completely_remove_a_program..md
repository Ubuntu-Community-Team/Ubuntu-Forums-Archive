---
title: "How do you completely remove a program."
date: 2011-06-17
forum: General Help
---

### Post by kmdent on 2011-06-17
Hi all,

My emacs editor is messed up so I tried to remove it via synaptic. It gave me an error and exited. Is there any way to manually remove that data so I can freshly re-install my favorite editor?!

Kyle

---

### Post by claracc on 2011-06-18
You can use in a xterm the command: sudo aptitude remove name_of_the_program, it will remove the program and its dependencies. You can see man aptitude for more options.

---

### Post by wildmanne39 on 2011-06-18
> **kmdent said:**
> Hi all,

My emacs editor is messed up so I tried to remove it via synaptic. It gave me an error and exited. Is there any way to manually remove that data so I can freshly re-install my favorite editor?!

KyleHi, 
```
sudo apt-get --purge remove packagename
```

---

### Post by doas777 on 2011-06-18
sudo apt-get purge appname

---

### Post by crispy_420 on 2011-06-18
Synaptic has the option of "Mark for Complete Removal".

---

### Post by gandaran on 2011-06-18
> **kmdent said:**
> Hi all,

My emacs editor is messed up so I tried to remove it via synaptic. It gave me an error and exited. Is there any way to manually remove that data so I can freshly re-install my favorite editor?!

Kyle
just deleting the apps user profile data in the hidden /home/'user' directory sometimes fixes things, no need to uninstall or re-install.

---

