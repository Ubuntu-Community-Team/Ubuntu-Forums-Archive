---
title: "Help with running a script"
date: 2010-10-23
forum: General Help
---

### Post by physic.dude on 2010-10-23
After I installed Ubuntu 10.10 on my computer, I installed all of my previous programs and when it came to a fractal program named Fr0sT... I forgot how to install it. 

In the source folder I downloaded I have an "install-dependencies.sh" file, "fr0st.py" file, and a few other files and folders. (I think I need to install the .sh file but I don't know how how)

I need to get this program installed, so any advice would be great

Fr0sT website:
[http://fr0st.wordpress.com/](http://fr0st.wordpress.com/)

---

### Post by physic.dude on 2010-10-23
bump

---

### Post by physic.dude on 2010-10-23
Bump


FYI, the father of this fractal geometry,  Benoit Mandelbrot has recently died from cancer on Oct. 14, 2010

[http://www.scientificamerican.com/blog/post.cfm?id=benoit-mandelbrot-dead-at-85-2010-10-18 ]("http://www.scientificamerican.com/blog/post.cfm?id=benoit-mandelbrot-dead-at-85-2010-10-18")

---

### Post by twodogs on 2010-10-23
right click the .sh file and tick the box 'allow executing file as program' then in terminal 'sudo sh ./name of file'  also, you could double-click this file and 'run in terminal.'

after that is installed, just run .py file to run program, I believe.

hope this helps.

---

### Post by physic.dude on 2010-10-23
I already tried that...

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

### Post by twodogs on 2010-10-23
haha I just saw your location.  Where in south Florida?

Anyway, do you have build-essential installed?  just 'sudo apt-get install build-essential' then try what I wrote before.  If that doesn't work I would just install the dependencies manually.  Can you give me the link to the same download of frost that you have and I will install on my Ubuntu.

---

### Post by twodogs on 2010-10-23
just found this...

[http://fr0st.wordpress.com/2010/05/22/installing-fr0st-in-ubuntu/](http://fr0st.wordpress.com/2010/05/22/installing-fr0st-in-ubuntu/)

---

