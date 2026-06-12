---
title: "Using dotdeb packages possible?"
date: 2006-06-06
forum: General Help
---

### Post by PeterB on 2006-06-06
Hi,

I seem to remember having used dotdeb.org packages on Warty, but when trying to do so on Dapper the entries in my /etc/apt/sources.list file are ignored.  Is there any way I can use Debian stable packages on Dapper?  dotdeb provides preferable PHP builds compared with those in the Ubuntu repositories.

Thanks!

---

### Post by shamrock_uk on 2006-06-06
[QUOTE=PeterB]Hi,

I seem to remember having used dotdeb.org packages on Warty, but when trying to do so on Dapper the entries in my /etc/apt/sources.list file are ignored.  Is there any way I can use Debian stable packages on Dapper?  dotdeb provides preferable PHP builds compared with those in the Ubuntu repositories.

Thanks![/QUOTE]

Could you clarify how exactly they are being ignored? Do you get an error when running apt-get update or can you just not install the packages? 

One possible explanation (and please excuse if i'm stating the obvious) if you're just running apt-get install xxxx is that the Dapper versions are more recent...you may have to select the package manually in Synaptic?

---

### Post by aysiu on 2006-06-06
Mixing Debian and Ubuntu repositories is a bad idea--a quick way to screw up your system.

---

### Post by PeterB on 2006-06-06
[QUOTE=shamrock_uk]Could you clarify how exactly they are being ignored? Do you get an error when running apt-get update or can you just not install the packages?[/quote]

When using apt-cache show XXX the new packages weren't showing up, neither were they listing in apt-cache show XXX |less

Running apt-get update produced a list of Hits but the dotdeb entries had **Ign** in front of the first 4.

> One possible explanation (and please excuse if i'm stating the obvious) if you're just running apt-get install xxxx is that the Dapper versions are more recent...you may have to select the package manually in Synaptic?

Ah, I am just running apt-get install xxxx - or apt-cache show xxxx to check the package that's registered in apt.

---

### Post by thasheep on 2006-06-06
I fail to see the reason for using dotdeb packages, but if you must, you could try creating/adding to /etc/apt/preferences. If the problem is that dotdeb uses older versions than dapper or you've configured apt to prefer dapper packages (a good idea), you could set the priority of the dotdeb ones higher. The following in /etc/apt/preferences should do the trick.
```
Package: *
Pin: origin packages.dotdeb.org
Pin-Priority: 991
```

---

### Post by PeterB on 2006-06-06
[QUOTE=aysiu]Mixing Debian and Ubuntu repositories is a bad idea--a quick way to screw up your system.[/QUOTE]
Thanks for the warning.  So unless I compile from source there's no way to get a wider range/more up-to-date packages?

---

### Post by PeterB on 2006-06-06
thasheep: dotdeb provides libapache-mod-php5, which Ubuntu doesn't (providing only Apache2 modules).

---

