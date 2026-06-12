---
title: "Help with installing GLUT"
date: 2006-04-16
forum: General Help
---

### Post by Zdravko on 2006-04-16
I tried to install the GLUT libraries, but after:
> 
./mkmkfiles.imake

I got:
> 
bash: ./mkmkfiles.imake: /bin/csh: bad interpreter: file or directory not found

What could be the problem?

---

### Post by xXx 0wn3d xXx on 2006-04-16
[QUOTE=Zdravko]I tried to install the GLUT libraries, but after:

I got:

What could be the problem?[/QUOTE]
Is it a tar.gz/bz2 file ? If so try this:

> cd /path/to/the/file

> ./configure

> make

> sudo make install

---

### Post by Zdravko on 2006-04-16
Yes, it is a tar archive. What should I do? I already extracted the archive on my desktop. In the README I read, that I have to navigate to the $GLUT_HOME and there execute the command. But it doesn't work! :(

---

### Post by Xenobia_Omega on 2006-06-15
[QUOTE=Zdravko]Yes, it is a tar archive. What should I do? I already extracted the archive on my desktop. In the README I read, that I have to navigate to the $GLUT_HOME and there execute the command. But it doesn't work! :([/QUOTE]


You need to install the C-Shell.

sudo apt-get install csh

---

### Post by Scratty on 2006-06-18
Why not simply bring up synaptic and install:
[LIST]
[*]freeglut3
[*]freeglut3-dbg
[*]freeglut3-dev
[/LIST]
(you probably don't need freeglut3-dbg).
?

---

