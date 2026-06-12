---
title: "Compiling software from source"
date: 2011-04-16
forum: General Help
---

### Post by ImDougy on 2011-04-16
I am confused with the whole compiling software thing. it works only sometimes when i type make and make install. could someone give me some links or tell me the ways to do this? i'd really appreciate it.

---

### Post by seawolf167 on 2011-04-16
First of all, ensure you have the packages you need to compile from source

```
sudo apt-get install build-essentials
```

Then, once you download source code, look for a README file and read up on that file. It will usually tell you what other packages or libraries you need to compile the package. You'll need to meet any unmet dependencies before you can compile the code without errors.

The general steps to compiling source code are:

```
./configure
make
sudo make install
```

You should take a look at *checkinstall* if you like compiling from source, as this makes it WAY easier to remove any source programs if you decide you don't need them anymore

```
sudo apt-get install checkinstall
```

then instead of running 

```
sudo make install
```

run this instead

```
sudo checkinstall
```

---

### Post by yetiman64 on 2011-04-16
> **ImDougy said:**
> I am confused with the whole compiling software thing. it works only sometimes when i type make and make install. could someone give me some links or tell me the ways to do this? i'd really appreciate it.

Some Community Documentation on the subject is at [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

I definitely agree it's easier to use checkinstall over install. It produces a .deb package and can be far easier to totally uninstall a program using Synaptic Package Manager.

---

### Post by ImDougy on 2011-04-20
thanks for the replies guys :) this helped alot.

---

### Post by SeijiSensei on 2011-04-20
One other hint is to use the "build-dep" directive to apt-get.  Suppose I wanted to build mplayer from source.  I can run

```
sudo apt-get build-dep mplayer
```

and apt will install all the development libraries needed to compile mplayer.  build-essential provides the basic tools, but complex programs have lots of other build dependencies which build-dep can usually take care of.

---

