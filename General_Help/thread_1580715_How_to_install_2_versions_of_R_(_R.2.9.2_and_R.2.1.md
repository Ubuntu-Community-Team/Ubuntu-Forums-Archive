---
title: "How to install 2 versions of R ( R.2.9.2 and R.2.11.1) in ubuntu"
date: 2010-09-23
forum: General Help
---

### Post by janaahan13 on 2010-09-23
Hi,
I'm new to ubuntu and I installed the latest version of R ( R.2.11.1) in my machine and I can run that by simply typing "R" in terminal but I need to install the old version of R ( R.2.9.2) since some packages don't support the new version. I have the .tar.gz file of old version. How can I install that? How do I run in terminal ?

---

### Post by gzarkadas on 2010-09-25
The .tar.gz is a source package. This is what you need in your case because the way to go is to install your old version in /usr/local, where source packages are installed by default. You will need the following:

1. Unpack the tar.gz to a directory of your choice (say ~/src/R):
```

mkdir -p ~/src/R
cd ~/src/R
gunzip -c [path-to-your-file]/[name-of-your-file].tar.gz  > [name-of-your-file].tar
tar xvf [name-of-your-file].tar

```2. Cd to the top directory of the source-tree (it will be the only directory inside ~/src/R after step 1); *_next commands assume you are there_*.

3. Install -with apt-get, synaptic, or whatever tool you use- before the configure phase all packages (tools and libraries) that are needed to compile and install R. This information is usually provided in the README or INSTALL files in the top directory of your source tree.

4. If the package does not provide a bootstrap script (it will state so in the files above), run:
```

./configure
make
sudo make install

```**IMPORTANT:** Before entering the next command, inspect the output for errors. You should not get errors from ./configure and make; make install will then fail or you will get a bogus application. Warnings are usually allowed.

5. If the package does provide a bootstrap script, you definitely must run it first. Then perform the step #4 actions.

6. Assuming all went well, you now have the new version in /usr/bin and the old version in /usr/local/bin. If your PATH variable (type echo $PATH in a terminal to see it) has /usr/local/bin in front of /usr/bin, then by default you call the old version and you will have to use /usr/bin/R (or whatever) to run the new one. 
If you want to change this, the best way IMO is to make a couple of symlinks with unique names (say newR, oldR) inside /usr/local/bin and use them to run the applications; it is less involved than changing your PATH and you know directly by the name what you call.

---

