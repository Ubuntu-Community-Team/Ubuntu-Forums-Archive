---
title: "Remastersys can not downloading for install"
date: 2010-12-03
forum: General Help
---

### Post by kema_u on 2010-12-03
Hi!

I add to source list this adres : 
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

But after reload the update manager gives this error :

W:Failed to fetch [http://www.geekconnection.org/remastersys/repository/dists/karmic///binary-i386/Packages.gz](http://www.geekconnection.org/remastersys/repository/dists/karmic///binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

And i can not see the remastersys package on synaptic manager ...

Can someone help me please ? 

Thank you!

---

### Post by Verbeck on 2010-12-03
remove the source and try installing from the .deb

[http://www.geekconnection.org/remastersys/repository/karmic/remastersys_2.0.17-1_all.deb](http://www.geekconnection.org/remastersys/repository/karmic/remastersys_2.0.17-1_all.deb)

just double click it after downloading  and the software center (in 10.10) or gdebi will prompt to install it

---

### Post by kema_u on 2010-12-03
> **Verbeck said:**
> remove the source and try installing from the .deb

[http://www.geekconnection.org/remastersys/repository/karmic/remastersys_2.0.17-1_all.deb](http://www.geekconnection.org/remastersys/repository/karmic/remastersys_2.0.17-1_all.deb)

just double click it after installing  and the software center (in 10.10) or gdebi will prompt to install it

No. if i do that, it will not update itself...

---

### Post by kema_u on 2010-12-03
This is my problem or remastersys s server are broken ? please i need help .. :(

---

### Post by 101011010010 on 2010-12-03
Hello, I just added Remastersys to Synaptic and got the same result. Hopefully it will be sorted soon.

---

### Post by kema_u on 2010-12-03
> **101011010010 said:**
> Hello, I just added Remastersys to Synaptic and got the same result. Hopefully it will be sorted soon.

How it is possible ? I can not add it.. :(

---

### Post by Verbeck on 2010-12-03
strange, i'm not having that problem
did you add through synaptic/software sources or directly to /etc/apt/sources.list ?

---

### Post by 101011010010 on 2010-12-03
Hello again, sorry I took so long. I added it via Synaptic. Exactly the same address as kema_u 's address in the first post.
> deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/A.

---

### Post by Verbeck on 2010-12-04
could you remove it from there and add it directly to your sources.list?
from a terminal:
```
gksu gedit /etc/apt/sources.list
```
then, on a new line enter
```
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/
```
again from a terminal 
```
sudo apt-get update
sudo apt-get install remastersys
```

if the problem persists, revert any changes

---

### Post by kema_u on 2010-12-05
Sorry... The answers takes long... I install the remastersys manualy from deb. There is no problem now...

Thank you!

---

### Post by COOLDUDEGAMER on 2010-12-08
Thanks for the download link Verbeck!

---

