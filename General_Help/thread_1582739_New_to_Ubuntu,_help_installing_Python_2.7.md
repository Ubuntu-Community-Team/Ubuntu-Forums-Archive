---
title: "New to Ubuntu, help installing Python 2.7"
date: 2010-09-26
forum: General Help
---

### Post by BrinKale on 2010-09-26
I am quite new to Ubuntu. I got tired of Windows and wanted to shake things up for myself a bit. Hopefully I can learn a few things as I go through this one by one.

The problem I am having right now; I would like to install Blender but, the package says it required Python (I assume it means any version equal to or above 2.5). I downloaded the Ubuntu 9.04 Deb Package (for Linux x86-64) located on [this](http://www.blender.org/download/get-blender/) page. I am attempting to install the Python 2.7 compressed source tarball from [this](http://www.python.org/download/) page but the furthest I could accomplish was extraction and running the configure file. I am at a loss as to what to do next.

Figured out what to do;

After running the configure file via terminal ( ./configure or sudo ./configure ), run the make command then make test followed up with a make install (I assume you can skip directly to make install). I got this from opening the makefile in a text editor. The first commented section of the file has the instructions. Hope this helped anyone who had similar problems.

---

### Post by dirghrabadia on 2010-09-26
You might try getting Blender from the Synaptic Package Manager, since it won't involve any command-line stuff.
But if you are interested, here is how one usually goes about:
Download the tarball, extract it, go to the new directory created, look for a READ ME file for instructions on compiling the source code. 
Hope that helps :)

---

