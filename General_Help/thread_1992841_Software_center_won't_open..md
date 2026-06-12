---
title: "Software center won't open."
date: 2012-06-01
forum: General Help
---

### Post by thedarkdragon65 on 2012-06-01
I have tried to run it with the commend: 

```
sudo software-center --enable-lp
```However, I get the following error:

```

File "/usr/bin/software-center", line 152
    print time.time()
             ^
SyntaxError: invalid syntax
```
This occurred after I installed Python 3 and made it the "default" python on the system. Any help would be great. Thanks.

---

### Post by shubham1 on 2012-06-01
might be the old python runs this syntax as valid but new does not try making old python the defualt and test it

---

### Post by psrdotcom on 2012-06-01
Hi,

Have you tried to re-install it using apt-get.

sudo apt-get install --reinstall software-center

---

### Post by thedarkdragon65 on 2012-06-01
After trying to reinstall it I get the following error:

```
E: Unable to locate package software-cent
```

---

### Post by oldos2er on 2012-06-01
The package name is **software-center**

---

### Post by lechien73 on 2012-06-01
According to this document:

[https://wiki.ubuntu.com/Python/FoundationsPPythonVersions](https://wiki.ubuntu.com/Python/FoundationsPPythonVersions)

Software Center is on Python 2.7. Currently Python 3 is not the default Python on Ubuntu 12.04 and may not be until 12.10 or 14.04.

---

### Post by thedarkdragon65 on 2012-06-01
> **lechien73 said:**
> According to this document:

[https://wiki.ubuntu.com/Python/FoundationsPPythonVersions](https://wiki.ubuntu.com/Python/FoundationsPPythonVersions)

Software Center is on Python 2.7. Currently Python 3 is not the default Python on Ubuntu 12.04 and may not be until 12.10 or 14.04.

Oh that probably explains why it isn't working. How can I set Python 2.7 back to my default? Thanks.

---

### Post by lechien73 on 2012-06-03
The previous version of python is probably still there, we just need to change a couple of things.

Please could you post the output of:

```
ls -l $(which python)
```

Thanks

---

### Post by thedarkdragon65 on 2012-06-03
> **lechien73 said:**
> The previous version of python is probably still there, we just need to change a couple of things.

Please could you post the output of:

```
ls -l $(which python)
```Thanks


Yea, the output is: 

```
lrwxrwxrwx 1 root root 7 May 29 23:54 /usr/bin/python -> python3
```

---

### Post by raja.genupula on 2012-06-03
ok use this to set your python to 2.7 
[http://stackoverflow.com/questions/5233536/python-2-7-on-ubuntu](http://stackoverflow.com/questions/5233536/python-2-7-on-ubuntu)

---

