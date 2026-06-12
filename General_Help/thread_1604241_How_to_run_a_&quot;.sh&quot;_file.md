---
title: "How to run a &quot;.sh&quot; file"
date: 2010-10-23
forum: General Help
---

### Post by physic.dude on 2010-10-23
I have a file I need to install on Ubuntu with  the extension .sh, the title is "install-dependencies.sh" so I am not sure how to treat it. 

Any help?  :confused:

---

### Post by SavageWolf on 2010-10-23
Right Click -> Properties -> Permissions -> Check "Allow Executing" -> Close Properties -> Double click.

---

### Post by physic.dude on 2010-10-23
nope, still does not work...

after I type my password I get this in return:

     
 ```
    sudo: aptitude: command not found
./install-dependencies.sh: line 26: svn: command not found
./install-dependencies.sh: line 28: pushd: flam3-2.8-src: No such file or directory
./install-dependencies.sh: line 29: aclocal: command not found
./install-dependencies.sh: line 30: automake: command not found
./install-dependencies.sh: line 31: autoconf: command not found
./install-dependencies.sh: line 32: libtoolize: command not found
./install-dependencies.sh: line 33: ./configure: No such file or directory
make: *** No rule to make target `clean'.  Stop.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./install-dependencies.sh: line 37: popd: directory stack empty
```

---

### Post by GlazedWicker on 2010-10-23
Go to Applications>Accessories>Terminal, navigate to the directory containing the install-dependencies.sh file, and type ./install-dependencies.sh

Edit: It looks like you're trying to compile something from source. Try

```
sudo aptitude install build-essential
```

---

### Post by physic.dude on 2010-10-23
> **GlazedWicker said:**
> Go to Applications>Accessories>Terminal, navigate to the directory containing the install-dependencies.sh file, and type ./install-dependencies.sh

Edit: It looks like you're trying to compile something from source. Try

```
sudo aptitude install build-essential
```

I actually am trying to install something from source...
But that line of code tells me this after I type my password.
```
sudo: aptitude: command not found

```

Could it be that I use Ubuntu 10.10 in 64 bit?

---

### Post by GlazedWicker on 2010-10-23
Hmm you could try reinstalling aptitude via Synaptic.

---

### Post by physic.dude on 2010-10-23
> **GlazedWicker said:**
> Hmm you could try reinstalling aptitude via Synaptic.

Awesome!!! It works now, you rock. :guitar:

---

### Post by GlazedWicker on 2010-10-23
Glad I could help.

---

