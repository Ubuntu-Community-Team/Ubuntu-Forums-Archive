---
title: "Help on installing Mattricks"
date: 2006-04-28
forum: General Help
---

### Post by Gamli on 2006-04-28
Hello ! 

I downloaded the .deb file of mattricks (hattrick manager) and used sudo dpkg -i mattricks.deb to install. But then I got the error 

```
dpkg: dependency problems prevent configuration of mattricks:
 mattricks depends on python (<< 2.4); however:
  Version of python on system is 2.4.2-0ubuntu3.
 mattricks depends on libwxgtk2.4-python; however:
  Package libwxgtk2.4-python is not installed.
dpkg: error processing mattricks (--install):
 dependency problems - leaving unconfigured

```

Then I installed the libwxgtk2.4-python and got the error 
```
Package libwxgtk2.4-python is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  python-wxtools python-wxgtk2.4

```
I installed the python-wxtools python-wxgtk2.4 but still I get the same errors and can not install mattricks.

---

