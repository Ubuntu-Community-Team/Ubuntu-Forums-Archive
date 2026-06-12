---
title: "Python Error after update to 11.04"
date: 2011-05-10
forum: General Help
---

### Post by bijanbina on 2011-05-10
hi
i update my ubuntu(10.10) to 11.04 when it update i got one error that say can not install python or upgrade . the installation finsh and i reboot my pc then ubuntu wont start i try to use ```
sudo dpkg --configure -a --force-all
```my system repair but i still Have problem with python

the real issue is that when i install a package that require python the package wont install and say error:
```
Package python is not configured yet
```

---

### Post by sabauma on 2011-05-11
I had the same problem after upgrading. I'm not sure how to fix the error with pycentral.

My final solution was to forcefully reconfigure all the packages with

```

sudo dpkg --configure -a --force-all

```

I still get the same error, but this way it will continue configuring all the other packages that need updating.

This gives me a running system to work with at least. Still seeing if I can get the underlying error resolved.

---

### Post by bijanbina on 2011-05-12
thanks i do this and it work !!!

my system start Now but have a lot problem can anyone find a better soulotion

---

### Post by bijanbina on 2011-05-12
hi again 
the real issue is that when i install a package that require python the package wont install and say error:
```
Package python is not configured yet
```and its because my python doesn't upgrade successfully from 2.6 to 2.7.1 and the error is:
```
Setting up python (2.7.1-0ubuntu5) ...
Linking and byte-compiling packages for runtime python2.7...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2330, in <module>
    main()
  File "/usr/bin/pycentral", line 2324, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1789, in run
    ignore_errors = self.options.ignore != None)
  File "/usr/bin/pycentral", line 1098, in install
    self.default_runtime.byte_compile(self.private_files, bc_option,
AttributeError: 'NoneType' object has no attribute 'byte_compile'


```

---

### Post by bijanbina on 2011-05-12
hi again 
the real issue is that when i install a package that require python the package wont install and say error:
```
Package python is not configured yet
```

---

### Post by bijanbina on 2011-05-13
[SIZE=3]Soulution:[/SIZE] 
You must delete any older version of python in synaptic then continue dpkg

---

