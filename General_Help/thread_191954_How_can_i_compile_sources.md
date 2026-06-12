---
title: "How can i compile sources?"
date: 2006-06-08
forum: General Help
---

### Post by rgreenfield on 2006-06-08
Hello everyone,

Forgive me if this is a "lame Q", though I am pretty new to Linux, and coming from a pure windows background where compiling is as easy as hitting a key or two I feel a little overwhelmed (](*,) ) with it on Linux. There's a lot of apps I would appreciate having installed, though they all need to be compiled.

Does anyone have a link to some nice ubuntish tutorials regarding compiling etc.? 

Best regards,
 -Ronald Greenfield

---

### Post by frodon on 2006-06-08
You can read the last part of this thread : [http://ubuntuforums.org/showthread.php?t=153118](http://ubuntuforums.org/showthread.php?t=153118)

---

### Post by medio on 2006-06-08
Are you sure you have to compile them all? 
Have you checked whether they are available in Synaptic Packet Manager?

---

### Post by thasheep on 2006-06-08
How the source is built and installed can vary, but it normally goes along the lines of.

Install build-essential and checkinstall 'sudo apt-get install build-essential checkinstall'
Download the source package, normally something.tar.bz2 or something.tar.gz
Unpack archive, on the command line, 'tar -jxf something.tar.bz2' or 'tar -zxf something.tar.gz', depending on the suffix.
```
cd something
less README   # read the readme :) up/down arrows to scroll, q to quit
less INSTALL   # read the install file - often useless :( and now, depending on what you've just read
./configure  # configure the source for compilation/installing. do './configure --help' for all options
If configure complains about something missing, it normally means you have to install (with apt-get/synaptic) the package whatever-its-complaining-about-[color=red]dev[/color].
make
sudo make checkinstall # if you just do 'make install' (the traditional way) then you won't be able to remove the package with synaptic/aptitue/adept/dpkg/apt-get.
```

---

