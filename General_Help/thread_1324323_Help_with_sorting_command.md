---
title: "Help with sorting command"
date: 2009-11-12
forum: General Help
---

### Post by emigrant on 2009-11-12
hi all,
can any one suggest me a way to sort all the packages in the .../apt/archive according to size of the packages.

i mean how to modify this, so the output will be a list of .debs sorted according to their file size

```
ls -lh *.deb | sort -b
```so far what i get is something like this:
```

.......

w-r--r-- 1 root root  113K 2008-08-08 14:35 libdca0_0.0.5-0.1_i386.deb
-rw-r--r-- 1 root root  116K 2008-08-28 14:34 ttf-oriya-fonts_1%3a0.5.4ubuntu2_all.deb
-rw-r--r-- 1 root root  116K 2008-08-29 15:34 libcommons-dbcp-java_1.2.2-1ubuntu1_all.deb
-rw-r--r-- 1 root root  117K 2008-09-05 15:35 libjna-java_3.0.4-0ubuntu2_i386.deb
-rw-r--r-- 1 root root  119K 2007-11-20 01:33 libcommons-modeler-java_2.0.1-4_all.deb
-rw-r--r-- 1 root root  1.1K 2008-11-19 19:35 default-jdk_1.6-30ubuntu4_i386.deb
-rw-r--r-- 1 root root  1.1K 2008-11-19 19:35 default-jre_1.6-30ubuntu4_i386.deb
-rw-r--r-- 1 root root  1.1M 2008-06-20 20:34 libfftw3-3_3.1.2-3.1ubuntu1_i386.deb
-rw-r--r-- 1 root root  1.1M 2008-07-02 21:34 libfreemarker-java_2.3.13+debian1-1_all.deb
-rw-r--r-- 1 root root  1.1M 2008-09-30 11:34 libxerces2-java_2.9.1-2ubuntu2_all.deb
-rw-r--r-- 1 root root  1.1M 2009-03-20 03:41 xchat-common_2.8.6-2.1ubuntu4_all.deb
-rw-r--r-- 1 root root  1.1M 2009-06-05 15:36 libnb-apisupport1-java_6.5-0ubuntu2.1_all.deb
-rw-r--r-- 1 root root   11M 2009-08-11 01:41 openjdk-6-jdk_6b14-1.4.1-0ubuntu11_i386.deb
-rw-r--r-- 1 root root   12K 2009-01-22 22:34 x11proto-input-dev_1.5.0-1ubuntu1_all.deb
-rw-r--r-- 1 root root  1.2K 2009-03-28 22:34 libgcj-bc_4.3.3-1ubuntu1_i386.deb

.........
```
thank you very much for your help.

---

### Post by Giblet5 on 2009-11-12
```
ls -s | sort -bgk1
ls -l | sort -bgk5
```

---

### Post by emigrant on 2009-11-12
thank you for your reply,
can you please explain what is bgk1.
and what if i want to modify my above command in the post one, by keeping all those information and want to sort according the values in the 4th column?

---

### Post by Giblet5 on 2009-11-12
> **emigrant said:**
> thank you for your reply,
can you please explain what is bgk1.
and what if i want to modify my above command in the post one, by keeping all those information and want to sort according the values in the 4th column?

Sure.

-b = ignore leading blanks
-g = standard numerical ordering sort
-k1 = sort on first field

```
man sort
```


A better command for the second form would be ```
ls -l | sort -bgk5,8
```

That will sort on the fifth AND eighth fields, so that any sizes that are identical will be sorted according to name as well.

---

### Post by emigrant on 2009-11-12
thank you very much, i got it now :)

---

