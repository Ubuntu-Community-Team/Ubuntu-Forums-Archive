---
title: "Installing Python 2.7.3 from Source."
date: 2012-05-29
forum: General Help
---

### Post by Senior_Buckethead on 2012-05-29
Hi All,

I am going to install Python 2.7.3 from source. Where should I put the installation folder before I make and install? What is the default directory for python installations?

It says in the 2.7.3 distribution readme
> 
To build Python, you normally type "make" in the toplevel directory

Which directory is the 'top level directory'?

---

### Post by kevdog on 2012-05-29
The top directory is just the directory you are compiling it from. By default, usually user compiled executables are installed into /usr/local/bin.  Libraries are usually installed to /usr/local/lib.

I believe /usr/local/bin should be contained in your %PATH% environment variable by default, however I would verify.

---

### Post by Senior_Buckethead on 2012-05-29
thanks for that.

Does that mean I should move the install folder to /usr/bin and run make and install from there?
> 
To build Python, you normally type "make" in the toplevel directory.
If you have changed the configuration, the Makefile may have to be
rebuilt.  In this case, you may have to run make again to correctly
build your desired target.  The interpreter executable is built in the
top level directory.


---

