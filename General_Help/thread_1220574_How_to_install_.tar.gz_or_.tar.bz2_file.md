---
title: "How to install .tar.gz or .tar.bz2 file?"
date: 2009-07-22
forum: General Help
---

### Post by H.K.Murmu on 2009-07-22
How to install .tar.bz2 or .tar.gz file in jaunty?

---

### Post by philcamlin on 2009-07-22
Extract as above

cd name-of-program

READ README
 	Code:
 	./configure
make
sudo make install

---

### Post by darolu on 2009-07-23
The steps philcamlin not always work (although is the most common method) and you would need to install other packages previous configuring, compiling and installing a program from source code (which is what philcamlin's instruction do).

Can you tell us what program are you trying to install? some programs are already compiled (like the firefox files you download from firefox.com) and ready to run; others need different commands (like some .sh programs).

All programs should (and most of them have them) have a manual and/or a install file you can read on any text editor (like gedit); open your tar file (or extract the files) and look for the INSTALL file, can be labeled as README too; you should find installation instructions there.

If you do need to compile with make you are going to need to install some packages first; depending on the program you want to install. Read the (possible) errors the ./configure gives you to find out what libraries you need. You may want to install the "build-essential" package which includes g++, make, libc6 and libc (dev) and dpkg-dev, which are basic tools to compile programs from source code and build your own packages; I also recommend installing "automake".

---

### Post by philcamlin on 2009-07-24
did you manage to get it to work ?

---

### Post by Cheesemill on 2009-07-24
A tar file is like a zip/rar file in Windows, it can contain absolutely anything.
Your question doesn't really make sense, it's like saying 'How do I install a zip file'.
So we need to know whats inside.
 
You can extract it using
```
 
tar -xvzf <filename>

```for .tar.gz or
```
 
tar -xvjf <filename>

```for tar.bz2
 
There will usually be a README file inside with further instructions. If you let us know what you're trying to install we can give you further help.
 
PS - Installing from a tar should be your very last resort for installing programs in Ubuntu, take a look here for more details:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

