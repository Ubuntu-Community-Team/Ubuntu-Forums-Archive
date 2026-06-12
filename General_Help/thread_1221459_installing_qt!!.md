---
title: "installing qt!!"
date: 2009-07-23
forum: General Help
---

### Post by harivittal.hk on 2009-07-23
hi!!
i am getting problems in installing qt4.5..at the end installation i am gettin a symbolic link problem...
i tried installing qt4 from synaptic manager..but it has got so many packages for qt4 tat comes close arround 900MB..so m gettin to knw what to do..
is thr any fault in my sdk file..i downloaded it from  trolltech.com..plz help.:)

---

### Post by abhilashm86 on 2009-07-24
> **harivittal.hk said:**
> hi!!
i am getting problems in installing qt4.5..at the end installation i am gettin a symbolic link problem...
i tried installing qt4 from synaptic manager..but it has got so many packages for qt4 tat comes close arround 900MB..so m gettin to knw what to do..
is thr any fault in my sdk file..i downloaded it from  trolltech.com..plz help.:)

go to home using nautilus, press ctrl+h, it shows hidden files, then search for .qt,(also search for similar qt applications),delete it from the system.
```

abhilash@abhilash:~$ ls -a -l .qt
total 20
drwxr-xr-x   2 abhilash abhilash  4096 2009-07-22 08:35 .
drwxr-xr-x 117 abhilash abhilash 12288 2009-07-24 09:44 ..
-rw-r--r--   1 abhilash abhilash   642 2009-07-22 08:35 qt_plugins_3.3rc
-rw-------   1 abhilash abhilash     0 2009-07-22 08:35 .qt_plugins_3.3rc.lock

```
Now try installing, you will be able to install........

---

### Post by abhilashm86 on 2009-07-24
after you delete .qt from home, install sdk, if not possible. post output of
```

ls -a -l

```
of the home directory........

---

