---
title: "virtualbox - system mode"
date: 2010-01-07
forum: General Help
---

### Post by cyracks on 2010-01-07
I have installed virutalbox on ubuntu 8.10 host computer ( intel dual core, 4G ram ). Inside virtualbox there are 2 virtual machines both almost the same: ubuntu 8.04 with latest server kernel. One machine is web server the other is mail server ( zimbra ). 

When VM mail server is running it consumes all procesor power on host computer. If I run top command inside VM mail server (guest) it shows me very high % of system mode (constantly above 70% ), so I assume that is the source of my problems. 

My question is how do I find out what is kernel doing and if anybody else have similar problems/solutions :)

example line of top
```

Cpu(s): 24.0%us, 75.7%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st

```

---

### Post by cyracks on 2010-01-08
The code belowe solved the situation:
> su zimbra
zmproxyctl start
zmproxyctl stop

I had exactly the same problem as described on this link:
[http://www.zimbra.com/forums/installation/19183-zimbra-nginx-process-defuncting-3000-times-per-second.html](http://www.zimbra.com/forums/installation/19183-zimbra-nginx-process-defuncting-3000-times-per-second.html)

---

