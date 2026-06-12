---
title: "Installing Gnomenu (need help!)"
date: 2009-08-25
forum: General Help
---

### Post by nukeaholic on 2009-08-25
i'm trying to install the Gnomenu item to my ubuntu but when i input the command 'make install' it try's to install but results with this:

install -d /etc/gnomenu /usr/bin/ /usr/lib \
    /usr/share /usr/lib/bonobo/servers
install: cannot change permissions of `/etc/gnomenu': No such file or directory
make: [install] Error 1 (ignored)
/bin/sh: cannot create /etc/gnomenu/prefix: Directory nonexistent
make: *** [install] Error 2

before you give any suggestions, there are some things that you may want to know

>the terminal is running in the directory '~/Desktop/gnomenu'
>i've extracted the folder (gnomenu) from the downloadfile
>i got version 1.9.9
>i have compiz
>iz sad now :(

any help plz?

---

### Post by danwood76 on 2009-08-26
What command are you executing to get to that stage?

If it is a make install have you remebered to do:
```

sudo make install

```
As you do not have permissions to write to the /etc directory by default.

---

### Post by nicedanmonkey on 2009-08-27
There is also a PPA for GnoMenu.

[https://launchpad.net/~gnomenu-team/+archive/ppa](https://launchpad.net/~gnomenu-team/+archive/ppa)

---

