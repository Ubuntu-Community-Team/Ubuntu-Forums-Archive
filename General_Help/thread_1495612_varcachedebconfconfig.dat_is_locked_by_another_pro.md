---
title: "/var/cache/debconf/config.dat is locked by another proces"
date: 2010-05-28
forum: General Help
---

### Post by fatbuttlarry on 2010-05-28
I was receiving this error in 10.04, and it was due to a deleted lock file.

Same as thread:
[http://ubuntuforums.org/archive/index.php/t-25443.html](http://ubuntuforums.org/archive/index.php/t-25443.html)

> /var/cache/debconf/config.dat is locked by another proces

I fixed it by recreating the dpkg lock file:

```
sudo touch /var/lib/dpkg/lock
```

If its already there:
```
sudo rm /var/lib/dpkg/lock
```
```
sudo touch /var/lib/dpkg/lock
```

I had deleted the lock file after a failed apt-get process.  I hope this helps others.

I then cleaned the package manager with:
```
sudo dpkg --configure -a
```
```
sudo apt-get clean
```

-Tres

---

### Post by Melony on 2012-07-04
Thanks a lot, works!

---

