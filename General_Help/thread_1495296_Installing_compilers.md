---
title: "Installing compilers"
date: 2010-05-27
forum: General Help
---

### Post by Gigus on 2010-05-27
How do you install compilers for ubuntu? (still new to this)

I'm finally making a leap into software programming and I need a good compiler to work 

with for my java and C++ class.

---

### Post by towheedm on 2010-05-27
> **Gigus said:**
> How do you install compilers for ubuntu? (still new to this)

I'm finally making a leap into software programming and I need a good compiler to work 

with for my java and C++ class.

The GNU Compiler Collection (gcc) will compile both of these.  It's in the repos and can be installed using the Synaptic package manager, or install it from the command line with:

```
sudo apt-get install gcc
```

You may also want to installed the Make utility:

```
sudo apt-get install make
```

You may need to install the developer's libraries for the libraries you're going to be referencing.

---

### Post by Serpher on 2010-05-27
You can use an IDE like codeblocks which you can install via the Software Center (Applications --> Software Center --> Programming), or if you want a compiler like yasm and nasm just run this in a terminal

```
sudo apt-get install yasm
sudo apt-get install nasm
```

You can then use those by going to the code and executing

```
yasm <code location
```



Also I'm not really a huge expert on this, but you can also use the make command, simply go to the root directory of the code (Must be in own directory), subdirectories are allowed to be there too for the code, and execute:

```
make
make install
```

---

### Post by Iowan on 2010-05-27
**build-essential** is another package I frequently see mentioned. **gcc** is already on my Jaunty laptop (without installing additional packages), but I haven't done much with it... yet. There's an informative How-To around here somewhere...

---

### Post by Gigus on 2010-05-27
Thanks guys I will try this all.

Thanks again.

---

### Post by Silviner on 2010-06-18
Hi Folks,
new to this  forum, just installed Ubuntu 10.04 Desktop, normally a windows user, but attempting to do some assembly stuff with nasm (boot sector code).

Anyway, I attempted to install nasm as describe in one of previous posts 

sudo apt-get install nasm and I get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nasm

Any ideas?

Thanks.

---

