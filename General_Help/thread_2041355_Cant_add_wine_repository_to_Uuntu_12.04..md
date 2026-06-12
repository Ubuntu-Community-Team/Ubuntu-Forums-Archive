---
title: "Cant add wine repository to Uuntu 12.04."
date: 2012-08-12
forum: General Help
---

### Post by Robert R on 2012-08-12
Hi, 

I have been trying to install wine and cant seem to be able to install(add) the repository to the other software sources tab.  

Im using instructions from  [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

the repository im trying to add is   [I]ppa:ubuntu-wine/ppa

[/I]The box doesn't allow me to apply the changes:

see the pic ??

can anyone help please...

thanks.

---

### Post by bluexrider on 2012-08-12
For 12.04 use 

```
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) precise main  

deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) precise main 
```

---

### Post by Robert R on 2012-08-12
Thanks it worked perfectly.

---

