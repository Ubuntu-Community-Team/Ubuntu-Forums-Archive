---
title: "/etc/init.d/xorg start : No such file or directory"
date: 2010-04-19
forum: General Help
---

### Post by waloshin on 2010-04-19
/etc/init.d/xorg start : No such file or directory

When the server boots i get a blinking cursor.

---

### Post by asmoore82 on 2010-04-19
First, the login service is gdm(Gnome Display Manager) and not "xorg."

Second, if you are using Ubuntu 9.10 or higher, gdm has been converted to an
[_**[COLOR="Purple"]Upstart[/COLOR]**_]("http://en.wikipedia.org/wiki/Upstart") job, so the command to start it is simply:
```
sudo start gdm
```

And finally, the "server" versions of Ubuntu do not ship with any graphical interface at all.

---

### Post by waloshin on 2010-04-19
> **asmoore82 said:**
> First, the login service is gdm(Gnome Display Manager) and not "xorg."

Second, if you are using Ubuntu 9.10 or higher, gdm has been converted to an
[_**[COLOR="Purple"]Upstart[/COLOR]**_]("http://en.wikipedia.org/wiki/Upstart") job, so the command to start it is simply:
```
sudo start gdm
```

And finally, the "server" versions of Ubuntu do not ship with any graphical interface at all.

Thank you, but when ever my server starts it loads everything, but there is no terminal. 

This is all I get: [IMG]http://i30.tinypic.com/dy1t9f.png[/IMG]

And i have to press crtl + alt + f1 to get into terminal.

---

