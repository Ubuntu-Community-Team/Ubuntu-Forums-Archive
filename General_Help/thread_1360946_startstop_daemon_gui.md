---
title: "start/stop daemon gui"
date: 2009-12-21
forum: General Help
---

### Post by leg on 2009-12-21
I went to my admin menu just now to turn off Tomcat and could not find the gui app that I expected to be able to use to do this. Does anyone know what I have to install to make this program available?

---

### Post by cariboo on 2009-12-22
There isn't a gui app for what you want, you can open an Applications-->Accessories-->Terminal and type depending on what version you are using:

```
sudo /etc/init.d/tomcat stop
```

for versions before 9.10 and

```
sudo service tomcat stop
```

for 9.10 and later.

---

### Post by leg on 2009-12-22
Has one been removed since a previous release as I definitely did used to do this. There was an app in one of the menus where I could turn on/off daemons (Mysql, Apache etc) through a GUI.

---

### Post by 3rdalbum on 2009-12-22
> **leg said:**
> Has one been removed since a previous release as I definitely did used to do this. There was an app in one of the menus where I could turn on/off daemons (Mysql, Apache etc) through a GUI.

Yes. It doesn't work with the new Upstart system. There will probably be a similar utility at some point in the future, but there currently isn't one as far as I'm aware.

---

### Post by leg on 2009-12-22
Ok thanks.

---

