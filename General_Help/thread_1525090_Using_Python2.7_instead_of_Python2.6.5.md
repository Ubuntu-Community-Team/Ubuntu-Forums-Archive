---
title: "Using Python2.7 instead of Python2.6.5"
date: 2010-07-06
forum: General Help
---

### Post by mahimahi42 on 2010-07-06
On my Acer Aspire One D250 running Ubuntu 10.04, I recently installed Python2.7 to play with. However, whenever I run ```
python
``` in the terminal, it opens the Python2.6.5 interpreter. Is there anyway I can have 2.7's interpreter open when I want to work from the terminal?

Thanks for all help!

---

### Post by mahimahi42 on 2010-07-06
Anyone have any ideas? Should I change the link to python in /usr/bin to the Python2.7 installation?

---

### Post by thybro on 2010-07-08
For using Python 2.7 
run: python2.7
ie,
python  --> python2.7
```
python2.7 ./your_code.py
```

---

### Post by dyuen on 2010-08-23
What if I want to install an external library to python 2.7? I tried to install lxml to python, but it only install to Python 2.6.5, but not not 2.7. Is there anyway to install to 2.7?

---

### Post by tartley on 2011-02-22
Hey.

One way to achieve this is to download the source tar or zip of the package you want to install, and run its setup.py using the python that you want to install it for.

For example, to install lxml for python 2.7, download lxml.zip, unzip it, cd into the created directory, and run:

```
$ python2.7 setup.py install

```


I presume that if you use this method to install pip (or easy_install) for Python2.7, then you could use them to install packages for python2.7, so long as you make sure the 2.7 version of pip (or easy_install) comes on your PATH before the other versions of pip.

There might be problems if Ubuntu built-in programs expect to find the 2.5 versions of pip first on your PATH. Be ready to back out the above experiment (i.e. revert your PATH to what it was) if it breaks things.

Is there a definitive guide for running other versions of Python on Ubuntu? I haven't found it yet.

---

