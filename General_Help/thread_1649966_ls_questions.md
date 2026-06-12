---
title: "ls questions"
date: 2010-12-20
forum: General Help
---

### Post by COKEDUDE on 2010-12-20
Why does the "-l" option in ls -laC not work? It doesn't display the date, the permissions, owner, size, or time. 

```
~ $ ls -laC
.
..
.adobe
b43-fwcutter_013-2_i386.deb
.bash_history
.bash_logout
bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb
```

Why does the "-C" option in ls -C not work? It does the same thing with and without the "-C" option. 

```
~ $ ls -C
b43-fwcutter_013-2_i386.deb                             Live_CD
bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb  mount
broadcom-wl-4.150.10.5                                  Music
broadcom-wl-4.150.10.5.tar.bz2                          Pictures
Desktop                                                 Public
Documents                                               Templates
Downloads                                               Videos
fakeroot_1.14.4-1ubuntu1_i386.deb                       wireless
firmware-b43-installer_4.150.10.5-4_all.deb             wl_apsta-3.130.20.0.o
launchpad-integration_0.1.38-1mint1_all.deb
```

```
 ~ $ ls
b43-fwcutter_013-2_i386.deb                             Live_CD
bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb  mount
broadcom-wl-4.150.10.5                                  Music
broadcom-wl-4.150.10.5.tar.bz2                          Pictures
Desktop                                                 Public
Documents                                               Templates
Downloads                                               Videos
fakeroot_1.14.4-1ubuntu1_i386.deb                       wireless
firmware-b43-installer_4.150.10.5-4_all.deb             wl_apsta-3.130.20.0.o
launchpad-integration_0.1.38-1mint1_all.deb
```

---

### Post by iponeverything on 2010-12-20
C and l conflict. C is also the default behavior, so it is working.

The first of the two in the option list will take precedence.

---

### Post by Habitual on 2010-12-21
Different Forum/Same Q. :D

in terminal type 
```

alias ls

```
and reply here with the output.

Thank you.

---

### Post by COKEDUDE on 2010-12-21
> **iponeverything said:**
> C and l conflict. C is also the default behavior, so it is working.

**The first of the two in the option list will take precedence.**

I think you have this backwards. 

```
~ $ ls -laC
.
..
.adobe
b43-fwcutter_013-2_i386.deb
.bash_history
.bash_logout
.bashrc
bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb

```

```
~ $ ls -aCl
total 5760
drwxr-xr-x 30 mint mint    1080 2010-12-21 01:31 .
drwxr-xr-x  3 root root      60 2010-12-16 19:40 ..
drwx------  3 mint mint      60 2010-12-16 19:48 .adobe
-rw-------  1 mint mint   16310 2010-12-09 17:01 b43-fwcutter_013-2_i386.deb
-rw-------  1 mint mint    1854 2010-12-21 01:31 .bash_history
-rw-r--r--  1 mint mint     220 2010-12-16 19:40 .bash_logout
-rw-r--r--  1 mint mint      20 2010-12-21 01:12 .bashrc
-rw-------  1 mint mint  895786 2010-12-09 18:41 bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb

```

> **Habitual said:**
> Different Forum/Same Q. :D

in terminal type 
```

alias ls

```
and reply here with the output.

Thank you.

```
~ $ alias ls
alias ls='ls --color=auto'

```

```
~ $ alias
alias grep='grep --colour=auto'
alias ls='ls --color=auto'
alias rmdi='rm -ri'

```

---

### Post by iponeverything on 2010-12-21
> I think you have this backwards. 

indeed.

---

