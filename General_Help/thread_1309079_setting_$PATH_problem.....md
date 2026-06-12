---
title: "setting $PATH problem...."
date: 2009-11-01
forum: General Help
---

### Post by emigrant on 2009-11-01
hi all,
i set a path like this:
```

PATH=$PATH:/home/emigrant/Documents/BashTest
export PATH
```

in /home/emigrant/.bashrc

but when i do

```
echo $PATH
```

i don't get the new path i added.
do i have to relogin?

thank you for your helps..

---

### Post by bogdan.veringioiu on 2009-11-01
Hi.
You have to open a new terminal, after you edit .bashrc, for you to  see the modifications of .bashrc.
.bashrc is executed on non-login shells, meaning when you open new terminals.
Bogdan

---

### Post by emigrant on 2009-11-01
yeah. thanks. its working :)

---

