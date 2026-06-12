---
title: "php problems"
date: 2011-09-29
forum: General Help
---

### Post by sajansen on 2011-09-29
hey
 
i have a fresh install of ubuntu 10.10 and want to use it as server...i had one running on the same computer and with the same version and gide ([https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) ) but i cant seem to get php running...i have tried with the php4 and the php5...
 
when i try to open a php page it just downloads it (without the extension???)
 
pleas help, thanks
sander

---

### Post by An Sanct on 2011-09-29
That tutorial is really badly outdated... try this

```
sudo apt-get install lamp-server^
```

If some things are already installed, it should just skip them.

---

### Post by SeijiSensei on 2011-09-29
Make sure the libapache2-mod-php5 package is installed.

---

### Post by mörgæs on 2011-09-29
Let's begin from the beginning. Did you boot the computer after installing PHP?

---

### Post by mörgæs on 2011-09-30
> **linux2001 said:**
> You must install php5
```

$sudo apt-get install php5-* 
```

No, that is an integral part of the LAMP installation.

---

