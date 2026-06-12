---
title: "How to convert RPM to debian?"
date: 2006-05-04
forum: General Help
---

### Post by Hoffmann on 2006-05-04
Hello:

Does anyone know a tutorial about converting RPM files to debian installation files?

Thanks,
Hoffmann

---

### Post by Jagot on 2006-05-04
Have a look at this page - a bit of the way down is the explanation:

[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by Sef on 2006-05-04
You need alien.  It will convert an .rpm to .deb

sudo apt-get install alien

---

### Post by testube_babies on 2006-05-04
```
sudo apt-get install alien
```
then
```
sudo alien [package_name].rpm
```

---

