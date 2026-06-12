---
title: "how do i install libreadline.so.4"
date: 2010-12-04
forum: General Help
---

### Post by penguin1029 on 2010-12-04
i am trying to run sheepshaver on ubuntu and i get this error
```
SheepShaver: error while loading shared libraries: libreadline.so.4: cannot open shared object file: No such file or directory

``` 
thank you,
Adrian

---

### Post by karthick87 on 2010-12-04
Type the following in terminal and then run **SheepShaver**

```
sudo ln -s /var/lib/libreadline.so.5 /var/lib/libreadline.so.4
```

---

### Post by penguin1029 on 2010-12-04
> **karthick87 said:**
> Type the following in terminal and then run **SheepShaver**

```
sudo ln -s /var/lib/libreadline.so.5 /var/lib/libreadline.so.4
```

it brings this up ```
ln: creating symbolic link `/var/lib/libreadline.so.4': File exists

``` then i type ```
SheepShaver
```
then this comes up on the terminal ```
SheepShaver: error while loading shared libraries: libesd.so.0: cannot open shared object file: No such file or directory

```

---

### Post by WorMzy on 2010-12-04
For that error you need to install libesd0, it can be found in the repositories.

```
sudo apt-get install libesd0
```

Note that karthick's earlier suggestion may work, but may cause unexpected behaviour/crashes while using the application. You may want to consider finding a more recent version of the applciation, or find a replacement.

---

### Post by penguin1029 on 2010-12-04
Thank you!!!

---

### Post by karthick87 on 2010-12-04
Mark it as [COLOR=Red][SOLVED][/COLOR]

---

