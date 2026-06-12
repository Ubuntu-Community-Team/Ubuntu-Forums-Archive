---
title: "k3b and monkeyaudio ape format"
date: 2006-01-20
forum: General Help
---

### Post by gts on 2006-01-20
I'm trying to install ape plugin for k3b: I execute ./configure and everything seems ok, but when I execute make, I see lots of errors...

I attach the make output...

Daniele

---

### Post by GeneralZod on 2006-01-20
Do

```

sudo apt-get install k3blibs-dev

```

and try  ./configure && make again.  Post any further errors here! :)

---

### Post by gts on 2006-01-24
Nothing to do... Errors posted...

---

### Post by GeneralZod on 2006-01-24
Double post.

---

### Post by GeneralZod on 2006-01-24
That's weird.  Try

```

sudo apt-get install k3blibs

```

If that doesn't work, then I'm afraid I'm out of ideas :/

---

### Post by gts on 2006-02-05
It doesn't work...

---

### Post by rysiek on 2006-02-05
problem solved today on this box. ;)

here's the procedure:
download the sources:
```
wget http://jaist.dl.sourceforge.net/sourceforge/k3b/k3bmonkeyaudioplugin-3.0.tar.bz2
```
untar them:
```
tar -xjf k3bmonkeyaudioplugin-3.0.tar.bz2
```
install the libs:
```
apt-get install k3blibs k3blibs-dev
```
make the necessary symlinks:
(this is the part you've been lacking, gts)
```
ln -s /usr/lib/libk3b.so.1.0.0 /usr/lib/libk3b.so
ln -s /usr/lib/libk3b.so.1.0.0 /usr/lib/libk3b.so.2
```
cd to the sources directory, configure, make and install:
```
cd k3bmonkeyaudioplugin-3.0
./configure
make
make install
```
cleanup the mess ;)
```
cd ../
rm -rf k3bmonkeyaudioplugin-3.0/
```

that should do the trick - id did on my box. ;)
should you have any further problems, join the k3b-users mailing list (accessible from the project's webpage) - they're really helpful, and they're really fast, helped me get this one to work during 12hrs.

Cheers
Mike

---

### Post by GabrielWolff on 2006-02-09
When typing ```
make
``` it gives me the following error message: ```
gabriel@ubuntu:~/k3bmonkeyaudioplugin-3.0$ make
make: *** No targets specified and no makefile found.  Stop
```.


Why? 

G

---

### Post by jaded_pl on 2007-05-25
I have the same problem - what to do?

---

