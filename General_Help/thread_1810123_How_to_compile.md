---
title: "How to compile?"
date: 2011-07-22
forum: General Help
---

### Post by stamatiou on 2011-07-22
Hey guys,
I would like to learn how to compile programs and kernel but I don't know how to start. I am absolute beginner in this section. I have found some tutorials on compiling (only programs) but there are only some commands but I would like to learn it in deep. Where can I start?

---

### Post by Chayak on 2011-07-22
> **stamatiou said:**
> Hey guys,
I would like to learn how to compile programs and kernel but I don't know how to start. I am absolute beginner in this section. I have found some tutorials on compiling (only programs) but there are only some commands but I would like to learn it in deep. Where can I start?

```
sudo apt-get install build-essential
```

That will get you the required tools.  There are tutorials on compiling kernels on the net so I'll steer towards installing programs from source.

You'll normally get a tar.gz so unpack it and go into the directory.
sudo ./configure
sudo ./make
sudo ./make install

you can combine the last two but that's best left to when you figure out what each step is doing.

I'd suggest getting a C/C++ programming book that will explain compiling and linking in depth.

---

### Post by stamatiou on 2011-07-22
> **Chayak said:**
> ```
sudo apt-get install build-essential
```That will get you the required tools.  There are tutorials on compiling kernels on the net so I'll steer towards installing programs from source.

You'll normally get a tar.gz so unpack it and go into the directory.
sudo ./configure
sudo ./make
sudo ./make install

you can combine the last two but that's best left to when you figure out what each step is doing.

I'd suggest getting a C/C++ programming book that will explain compiling and linking in depth.
I am already learning C but is it the same? Will the program after that be on the menus?

---

### Post by lisati on 2011-07-22
Although C++ has a historical connection with C, it's often more useful to think of them as separate languages. The procedure for compiling them is similar.

As for adding programs to the menu, whether or not this happens can depend on the compilation script.

---

