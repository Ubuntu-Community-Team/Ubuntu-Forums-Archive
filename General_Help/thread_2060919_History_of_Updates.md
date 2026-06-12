---
title: "History of Updates"
date: 2012-09-21
forum: General Help
---

### Post by Kissell on 2012-09-21
I want to check from the command line what updates have been installed, sorted by timestamp.  

I suspect a server hasn't been updating, and need to be able to prove it.

thanks

---

### Post by drmrgd on 2012-09-21
There is an apt history log in /var/log/apt. It's not super informative.  But, it does show all the packages that were installed and removed, clustered by date.

---

### Post by wojox on 2012-09-21
```
cat /var/log/dpkg.log
```

You could grep it to filter:
```
cat /var/log/dpkg.log | grep 'install '
```

---

### Post by Kissell on 2012-09-21
Thanks, I'll take a look at that in a little bit.

---

