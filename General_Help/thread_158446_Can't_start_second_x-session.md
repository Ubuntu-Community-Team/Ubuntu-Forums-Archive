---
title: "Can't start second x-session"
date: 2006-04-11
forum: General Help
---

### Post by OldPlanet on 2006-04-11
I am already running X, and I want to start a second session with another DE/WM. If i try to run for example:
```
startx /usr/bin/startkde -- :1
```
I get this error:
```
xauth:  creating new authority file /home/oldplanet/.serverauth.8054
X: user not authorized to run the X server, aborting.
xinit:  Server error.
Couldnt get a file descriptor referring to the console
```

Some help would be appreciated. :)

---

### Post by jdong on 2006-08-18
sudo dpkg-reconfigure -plow x11-common


Choose "Anyone" instead of Console Users Only.

---

