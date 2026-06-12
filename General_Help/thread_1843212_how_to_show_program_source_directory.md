---
title: "how to show program source directory"
date: 2011-09-13
forum: General Help
---

### Post by wiswit on 2011-09-13
):P I am new to linux. I have to configure my R program to install a RPy application so that R call be called from within python. But where can I find the R source directory in ubuntu? Any idea would be appreciated. ~~

Thanks!

---

### Post by zackwasa on 2011-09-13
Can you please be more specific? What's *my R program*?

The source is there where you put it I think

---

### Post by wiswit on 2011-09-13
Thanks!!
R is an open source software mainly for statistics. 
I installed R on my ubuntu by sudo apt-get install R, but I don't know where the system put its source code? like what you have when you install from a tarball... you configure and make...

---

### Post by coldraven on 2011-09-13
Try this:
Open the Synaptic Package Manager, search for "R", then right click select "Properties" and click the "Installed Files" tab

---

### Post by fdrake on 2011-09-13
try :
```
locate R
whereis R
```

---

### Post by SeijiSensei on 2011-09-13
When you install a .deb package, there is no source code included.  Only the compiled binary and any associated files like man pages are installed.

Nearly all applications are installed to /usr/bin, with associated libraries in /usr/lib, and support files in /usr/share.  Some configuration files might be installed to /etc.

However I suspect you just need to install an associated package, [python-rpy]("http://packages.ubuntu.com/lucid/python-rpy").  Try running "sudo apt-get install python-rpy" at a command prompt.  Does that fix your problem?

I recommend becoming familiar with the package manager on your system.  You might consider installing synaptic ("sudo apt-get install synaptic") which is a very full-featured GUI manager.  Then you can search the list of packages for keywords like "R" or "python" and see what's available.

---

