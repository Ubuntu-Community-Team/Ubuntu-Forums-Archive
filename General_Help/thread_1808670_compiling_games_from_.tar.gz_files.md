---
title: "compiling games from .tar.gz files"
date: 2011-07-20
forum: General Help
---

### Post by killer62491 on 2011-07-20
just need to know how i would do this, I've tried it before, and I've gotten the following error, no matter what i tried: 
"make: *** No targets specified and no makefile found.  Stop."
solutions appreciated.

---

### Post by Gyokuro on 2011-07-20
have you already installed build-essentials?

sudo apt-get install build-essentials

or please let us know which game you want to compile.

---

### Post by seawolf167 on 2011-07-20
> **killer62491 said:**
> just need to know how i would do this, I've tried it before, and I've gotten the following error, no matter what i tried: 
"make: *** No targets specified and no makefile found.  Stop."
solutions appreciated.

As posted above, ensure you have

```
sudo apt-get get install build-essentials
```installed. Then always check for a README file in the archive after extraction. i.e.

```
tar xvzf filename.tar.gz
```Now look for a readme file or installation instructions file.

Then you usually have to do a 

```
./configure
make
sudo make install
```

I also suggest taking a look at the program *checkinstall* if you plan to install a lot of things from source

```
sudo apt-get install checkinstall
```

then just substitute the *checkinstall *command in for the *install *command

---

