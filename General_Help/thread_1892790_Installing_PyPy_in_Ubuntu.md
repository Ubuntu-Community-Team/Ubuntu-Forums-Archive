---
title: "Installing PyPy in Ubuntu"
date: 2011-12-08
forum: General Help
---

### Post by wes_one on 2011-12-08
Ok recently I started working with python and pretty much fell in love with it straight away.But since I also only started using Ubuntu OS it is very confusing to install some applications.Today I tried to install PyPy.

What I did is as it was written in their documentation.I un-rared/extracted/un-packaged the tar.bz2 file in the wanted folder and tried to run the PyPy from /bin folder.When I try to do so I get the following error:

./pypy: error while loading shared libraries: libssl.so.0.9.8: cannot open shared object file: No such file or directory

I tried to run it from terminal using the the following commands:

cd /home/vanio/Desktop/PyPy-1.7/bin
./pypy


Also I extracted/un-tared the pypy with tar xf /path/to/tar


So can anyone tell me how to do this?

---

### Post by lisati on 2011-12-08
*Thread moved to **General Help**.*

---

### Post by SevenMachines on 2011-12-09
Short answer is that you need libssl0.9.8 installed. For example,
```
# pypy won't start
$ ./pypy 
./pypy: error while loading shared libraries: libssl.so.0.9.8: cannot open shared object file: No such file or directory

# install apt-file, it's useful for finding things, 
# you can search at packages.ubuntu.com too if you like
$ apt-file search libssl.so.0.9.8
libssl0.9.8: /lib/libssl.so.0.9.8
libssl0.9.8: /usr/lib/libssl.so.0.9.8
libssl0.9.8-dbg: /usr/lib/debug/lib/libssl.so.0.9.8

$ sudo apt-get install libssl0.9.8
$ ./pypy 
Python 2.7.1 (7773f8fc4223, Nov 18 2011, 18:47:10)
[PyPy 1.7.0 with GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
And now for something completely different: ``All exceptblocks seem sane.''
>>>> 
```Note, there is a ppa too if you like that sort of thing
[https://launchpad.net/~pypy/+archive/ppa]("https://launchpad.net/%7Epypy/+archive/ppa")

---

