---
title: "reinstalling package"
date: 2009-07-02
forum: General Help
---

### Post by metalfan_ on 2009-07-02
Hi,

im trying to get a fresh /etc/apache2 folder. So i did

```

sudo /etc/init.d/apache2 stop
sudo mv /etc/apache2 /etc/apache2.old
sudo aptitude reinstall apache2

```

which did not create /etc/apache2.

Ok, lets see
```

dpkg -S /etc/apache2
apache2.2-common: /etc/apache2

```

There we go, a nobrainer...
```

sudo aptitude reinstall apache2.2-common

```

That was easy, lets just start apache now.
```

sudo /etc/init.d/apache2 start
.: 44: Can't open /etc/apache2/envvars

```

Hey, im stuck again.
Cant be that hard

```

dpkg -S /etc/apache2/envvars  
(the file isnt there, i just put this up for dpkg)
apache2.2-common: /etc/apache2/envvars

```

so why isnt it there? i just reinstalled the package?

---

