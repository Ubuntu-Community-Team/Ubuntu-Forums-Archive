---
title: "NumPy, SciPy, &amp; MatplotLib Installation Problems"
date: 2011-01-28
forum: General Help
---

### Post by JohnnySage50307 on 2011-01-28
Recently I've been playing with NumPy, SciPy, and MatplotLib on my Windows machine at work and wanted to install it on my Ubuntu machine at home.  I've used Synaptic and installed everything, yet when I write 
```
import numpy
```
I get an error that the module cannot be found.

Using 'find', it located NumPy at /usr/include/numpy, MatplotLib at /usr/share/matplotlib and could not find Scipy.  Adding these locations to PYTHONPATH did not help.

How do I correct this?

---

### Post by JohnnySage50307 on 2011-01-28
Recently, checking the MatplotLib site, I did
```
sudo apt-get install python-matplotlib
```
and it once again installed like how I described previously.

In my Python scripts, typing
```
import matplotlib
```
kicks back at me
```
Traceback (most recent call last):
   File "<stdin>", line 1 in <module>
ImportError: No module named matplotlib
```

However, if I run "ipython -pylab", the examples I use there work out well.  Also, if I write a script and import it through there, everything works out alright.  This really isn't how I'd like to run things.  The MatplotLib explains how to modify the matplotlibrc file so that it can run in the interactive interpreter, but this has not corrected the situation.

Nor has any of this actually corrected my problems using NumPy or SciPy.

Again, all help is highly appreciated!

---

