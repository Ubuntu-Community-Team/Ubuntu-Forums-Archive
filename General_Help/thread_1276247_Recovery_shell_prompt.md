---
title: "Recovery shell prompt"
date: 2009-09-26
forum: General Help
---

### Post by screaminfakah on 2009-09-26
is there a way to download and install packages through synaptic when you are in the recovery shell prompt with networking?

---

### Post by credobyte on 2009-09-26
```
sudo apt-get install <package>

```

---

### Post by screaminfakah on 2009-09-26
It worked.  I was forgetting install in the command

Thanks

---

### Post by lswb on 2009-09-26
Not with synaptic, but you can use the command line with apt as credobyte has noted and there is also the vt/curses program "aptitude"

---

