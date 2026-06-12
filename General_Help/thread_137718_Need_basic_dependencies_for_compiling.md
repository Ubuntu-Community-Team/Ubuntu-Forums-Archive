---
title: "Need basic dependencies for compiling"
date: 2006-02-28
forum: General Help
---

### Post by tajmox on 2006-02-28
Can someone give me an apt-get command for downloading all the required packages needed to compile programs for X, SDL, Gnome, K, etc?  
Ubuntu didn't even come with gcc, but I did get the build-essential package, and I still can't compile anything.

Thanks!

---

### Post by yanik on 2006-02-28
cd into the directory of the source and do these::

```
sudo -s
apt-get install auto-apt
auto-apt update
auto-apt updatedb
auto-apt update-local
auto-apt run ./configure
./configure
apt-get install checkinstall
checkinstall -D make install
```

---

### Post by mirons on 2006-02-28
There are bunches of packages. Everything ending with '-dev' is needed to compile something. Basics are (but is just according to my needs)
libglib2.0-dev
libgtk2.0-dev
libncurses5-dev
libqt3-mt-dev
They wil carry dependencies.

---

### Post by tajmox on 2006-02-28
You both just made my day, thank you and much love!

One more thing,
the command to list all available packages with apt-get?
Thanks

---

