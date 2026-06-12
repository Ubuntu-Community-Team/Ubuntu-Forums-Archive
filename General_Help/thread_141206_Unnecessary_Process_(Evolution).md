---
title: "Unnecessary Process? (Evolution)"
date: 2006-03-07
forum: General Help
---

### Post by jTHEn on 2006-03-07
I noticed that the process titled "evolution-exchange-storage" eats up quite its share of Virtual Memory, but I do not know if it is necessary to have running. I don't use the Evolution email program itself, but I know bits of evolution are needed for other desktop processes. Can anyone tell me if this process needs to be running? :-k

Many thanks

---

### Post by aysiu on 2006-03-07
It's described as > Exchange plugin for the Evolution groupware suite If you don't use Evolution, I can't imagine you'd need it. I just uninstalled it on my test Ubuntu partition, and nothing tragic happened.

It will, however, uninstall the *ubuntu-desktop* package, which means you won't be able to properly upgrade to Dapper when it comes out. Before Dapper comes out, make sure you apt-get *ubuntu-desktop* before doing a ```
sudo apt-get dist-upgrade
```

---

