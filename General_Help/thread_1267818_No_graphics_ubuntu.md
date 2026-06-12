---
title: "No graphics ubuntu"
date: 2009-09-16
forum: General Help
---

### Post by m4tic on 2009-09-16
I installed a sis driver .deb package, as it turns out it doesn't work. What can i do to revert to default settings? Or can accessing computer janitor help? I have a command line only

---

### Post by nothingspecial on 2009-09-16
```
sudo dpkg -r *[COLOR="Red"]packagename[/COLOR]*
```

restart

```
sudo shutdown -r now
```

and see if that helps, don`t kow if it will though.

---

### Post by m4tic on 2009-09-16
It says the package is not installed

---

### Post by 3rdalbum on 2009-09-16
> **m4tic said:**
> It says the package is not installed

Just the first part of the name; for instance, if the package was called "sis-driver_0.4.1_i386.deb", then just put:

```
sudo apt-get remove --purge sis-driver
```

---

### Post by m4tic on 2009-09-16
I didn't find anything. Here's the link to that package: 
 
[http://ncc-1701a.homelinux.net/~linux-sis/downloads/sis3d-driver-satux.deb](http://ncc-1701a.homelinux.net/~linux-sis/downloads/sis3d-driver-satux.deb)

---

