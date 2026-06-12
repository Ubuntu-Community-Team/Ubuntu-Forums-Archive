---
title: "GUI for apache"
date: 2010-12-06
forum: General Help
---

### Post by Vexiphne on 2010-12-06
Does anyone know of a simple gui for Apache that I can use to stop and start apache when I need it. I just installed apache on my laptop so I can work and test locally.

I tried webmin but it's to bloated.

---

### Post by Vexiphne on 2011-01-04
*bump*

---

### Post by Smart Viking on 2011-01-04
A GUI just to start and stop it? Isn't it just much easier to do
```

sudo /etc/init.d/apache2 start
sudo /etc/init.d/apache2 restart
sudo /etc/init.d/apache2 stop

```

---

### Post by Vexiphne on 2011-01-04
> **Smart Viking said:**
> A GUI just to start and stop it? Isn't it just much easier to do
```

sudo /etc/init.d/apache2 start
sudo /etc/init.d/apache2 restart
sudo /etc/init.d/apache2 stop

```

Is there a way to make a script that when I start it, it will give me a choice to select one of those 3? and enter the root code so I don't have to every time :)

---

