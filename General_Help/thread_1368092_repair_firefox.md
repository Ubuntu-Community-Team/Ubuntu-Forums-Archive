---
title: "repair firefox"
date: 2009-12-30
forum: General Help
---

### Post by tempus on 2009-12-30
I managed to break the installation of firefox in 9.04. I tried to repair the installation with no success. When i clicked on the icon it tells me that no such directory exists. How can i fix this?

---

### Post by zey on 2009-12-30
> **tempus said:**
> I managed to break the installation of firefox in 9.04. I tried to repair the installation with no success. When i clicked on the icon it tells me that no such directory exists. How can i fix this?


reinstall firefox would be a good option..
don't forget to delete .mozilla folder to before reinstall.

---

### Post by tempus on 2009-12-30
> **zey said:**
> reinstall firefox would be a good option..
don't forget to delete .mozilla folder to before reinstall.

that did not work. reinstalled with same problem after.

---

### Post by khelben1979 on 2009-12-30
Have you tried:

```
sudo apt-get remove firefox-3.5
```
and then
```
sudo apt-get install firefox-3.5
```

Also make sure that you have Mozilla firefox version 3 in the system, since I've received information that the Mozilla-3.5 package requires the older version in the system to work properly, please correct me if I'm wrong.

---

### Post by tempus on 2009-12-30
> **khelben1979 said:**
> Have you tried:

```
sudo apt-get remove firefox-3.5
```
and then
```
sudo apt-get install firefox-3.5
```

Also make sure that you have Mozilla firefox version 3 in the system, since I've received information that the Mozilla-3.5 package requires the older version in the system to work properly, please correct me if I'm wrong.

your instructions were of no help. Still does not work.

---

