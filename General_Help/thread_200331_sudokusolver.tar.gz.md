---
title: "sudokusolver.tar.gz"
date: 2006-06-20
forum: General Help
---

### Post by CameronCalver on 2006-06-20
i got sudokusolver.tar.gz form linux format magazine and i extracted it and it came out files with a executable file how do i open it

---

### Post by mlind on 2006-06-20
most apps need ./configure && make && make install to get them work.

You can use ./configure --prefix=$HOME, so you can install it locally without root
privileges.

For running binaries you need to make sure it has executable flag on and then just
type in the file name: for example running my_script executable 

```

chown 700 myscript
./my_script

```

You can also build .deb package out of it which is somewhat tougher task
[http://www.debian.org/doc/maint-guide/ch-start.en.html](http://www.debian.org/doc/maint-guide/ch-start.en.html)

---

### Post by CameronCalver on 2006-06-20
look at screen shot and look at this

cameron@ubuntu:~$ cd /home/cameron/downloads/sudokusolver-0.1
cameron@ubuntu:~/downloads/sudokusolver-0.1$ chmod 700 sudokusolver cameron@ubuntu:~/downloads/sudokusolver-0.1$ ./sudokusolver ./sudokusolver: error while loading shared libraries: libqt.so.3: cannot open shared object file: No such file or directory
cameron@ubuntu:~/downloads/sudokusolver-0.1$

and i posted the attatchement

---

### Post by Abild on 2006-06-20
This should do the trick:
```

sudo apt-get install libqt3-mt
cd /usr/lib
sudo ln -s libqt-mt.so.3 libqt.so.3

```

---

### Post by CameronCalver on 2006-06-21
yep thanks it works

---

