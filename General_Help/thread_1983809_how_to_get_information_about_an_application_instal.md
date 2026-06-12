---
title: "how to get information about an application installation"
date: 2012-05-20
forum: General Help
---

### Post by naftali mich on 2012-05-20
New to Linux. When I install an application with apt-get, I'd like to print to a text file the installation details, namely, the locations where the application's files are stored. I didn't see anything in the apt-get man page which said how to do it. If  it can't (easily) be done at installation, is there an easy way to aggregate that data after the fact? Some applications provide it in the about section but some do not.   

Thanks for your help.

---

### Post by Cheesemill on 2012-05-20
```
dpkg -L <package>
```
To find which package a particular file belongs to you can do:
```
dpkg -S <filename>
```

---

### Post by naftali mich on 2012-05-20
Perfect. Thank you so much.

---

