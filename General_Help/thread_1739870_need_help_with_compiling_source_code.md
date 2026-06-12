---
title: "need help with compiling source code"
date: 2011-04-26
forum: General Help
---

### Post by U235master on 2011-04-26
most programs that i want to install are just source code, and i follow all the instructions, but it always stops at make. it gives me this every time:
```
make: *** No targets specified and no makefile found.  Stop.

```
this has happened with every program i have tried to compile, such as zsnes, swfdec, f4l, sdl, alsa, and mrtg

---

### Post by TeoBigusGeekus on 2011-04-26
Have you installed build-essential?
```
sudo apt-get install build-essential
```

---

### Post by nothingspecial on 2011-04-26
> **U235master said:**
> 
```
make: *** No targets specified and no makefile found.  Stop.

```


You have to be in the directory the makefile is in.

---

### Post by U235master on 2011-04-26
yes i have, and i was trying to install swfdec, and i still get the same error


off topic: i loled at your avatar

---

### Post by U235master on 2011-04-26
> **nothingspecial said:**
> You have to be in the directory the makefile is in.
i am. i always cd to the directory that has the configure file in it

---

### Post by nothingspecial on 2011-04-26
Then what does the README say, sometimes there is an install.sh or similar

---

### Post by TeoBigusGeekus on 2011-04-26
Can you give us a link of the tarball you're trying to install?

---

### Post by U235master on 2011-04-26
the readme for swfdec tells me to run
```
./configure; make; make install;
```
and it still gives me the error

---

### Post by nothingspecial on 2011-04-26
Does ./configure give any errors?

---

### Post by nothingspecial on 2011-04-26
I'm guessing you haven't got the dependencies installed. Look at what the ./configure errors are saying, install the necessary packages and try again.

---

### Post by U235master on 2011-04-26
it says i need 
```
glib-2.0, gobject-2.0 and gthread-2.0 >= 2.16
```
i got glib-2.0 from apt-get but the others i dont know where or how to get them

---

### Post by TeoBigusGeekus on 2011-04-26
Try to find them with Synaptic Package Manager.

---

### Post by nothingspecial on 2011-04-26
Try python-gobject-dev

---

