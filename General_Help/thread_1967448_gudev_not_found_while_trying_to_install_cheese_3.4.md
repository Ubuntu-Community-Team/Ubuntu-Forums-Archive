---
title: "gudev not found while trying to install cheese 3.4.1"
date: 2012-04-28
forum: General Help
---

### Post by IdanSuper on 2012-04-28
while install cheese from the terminal after the command: ./configure i found this error: checking for gudev-1.0... configure: error: gudev-1.0 not found
how to solve it? thanks for help!

---

### Post by xyzzyman on 2012-04-28
To make it easier, instead of compiling for source just add the gnome3 team's PPA, it'll add everything from gnome 3.4 that didn't make release:

```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get upgrade
```

EDIT: Oh wait, it's already in the 12.04 repositories, and they haven't added it for 11.10 or older. You need to

```
sudo apt-get install gir1.2-gudev-1.0
```

What version of Ubuntu are you on? You may also run into other dependency issues not being on gnome 3.4.

---

### Post by IdanSuper on 2012-04-28
i'm on ubuntu 12.04 the newest, and I don't use gnome i'm using unity..

---

### Post by xyzzyman on 2012-04-28
Unity is based on gnome and uses it as its backbone. You just need to

```
sudo apt-get install cheese
```

It's already version 3.4.1 on Precise. :) That's the nice part about Ubuntu is you can install from the command line, or just go into Software Center and search for it and click to install right in the GUI. Unless you start getting into uncommon stuff, the regular desktop user doesn't have to compile anything.

---

### Post by IdanSuper on 2012-04-28
yes it works! thanks for help.. will change it to solved!

---

### Post by markenaix on 2012-07-08
> **xyzzyman said:**
> To make it easier, instead of compiling for source just add the gnome3 team's PPA, it'll add everything from gnome 3.4 that didn't make release:

```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get upgrade
```EDIT: Oh wait, it's already in the 12.04 repositories, and they haven't added it for 11.10 or older. You need to

```
sudo apt-get install gir1.2-gudev-1.0
```What version of Ubuntu are you on? You may also run into other dependency issues not being on gnome 3.4.

Hi,

I ran onto the same **missing gudev-1.0** when trying to install gnome-pilot-2.91.93 on an Ubuntu 12.04 in a Gnome 3.4.1 session even though **gir1.2-gudev-1.0 is installed** and I have the **ppa:gnome3-team/gnome3 repository** in my software sources.

Would appreciate your help cause I'm stuck in the ./configure step of the install.

Thanks in advance.

Some extra information:

```
sudo ldconfig -p | grep -i gudev
    libgudev-1.0.so.0 (libc6) => /usr/lib/i386-linux-gnu/libgudev-1.0.so.0

```

```
 sudo pkg-config --list-all | grep -i gudev
    gudev-sharp-1.0                GUdev - GUdev

```

---

