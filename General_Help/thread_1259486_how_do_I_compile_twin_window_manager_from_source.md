---
title: "how do I compile twin window manager from source?"
date: 2009-09-06
forum: General Help
---

### Post by pythonscript on 2009-09-06
I'm trying to install the twin window manager from source, but for the life of me, I can't figure out what problem it keeps having. I downloaded the latest version from the website 

[http://linuz.sns.it/~max/twin/]("http://linuz.sns.it/%7Emax/twin/")
For some reason, the development version has a lower version number than the stable version, but I downloaded version 0.6.1. I extract the tar file, cd into the new directory, and run

```
./configure
``` which seems to run fine, but make returns some errors which cause checkinstall to fail later on. I attached the output from configure and make, too. Can anyone help? I also tried the 0.5.1 version, that configure didn't even do anything. It paused for a split second and then popped me back to the terminal. Thanks for the help! I'd really like to get this working for my command line only ubuntu. 

[ATTACH]127664[/ATTACH]
[ATTACH]127665[/ATTACH]

EDIT: Also, didn't twin used to be in the repositories? I guess it's been removed in Jaunty, eh?

---

### Post by pythonscript on 2009-09-06
Anyone have any ideas? This looks like a really slick app, and I'd love to have it working. It'd definitely make my command line only ubuntu installation a lot nicer for every day use.

---

### Post by c0mput3r_n3rD on 2009-09-06
```

./configure
make
make install

```

If you look at the man pages or online references on the make command and compiling from source you'll find out exactly how to do it.

---

### Post by pythonscript on 2009-09-06
make returns errors, though, and running make install doesn't do anything different than make, because make returned a bunch of errors. My attachments have the error messages, if that proves helpful. I know the three basic commands for compiling from source, but I couldn't get make to work. Any ideas? Thanks!

---

### Post by nothingspecial on 2009-09-06
I`m not sure if this is the thing you want, but

```
sudo apt-get install dvtm
```

Then

```
dvtm
```

Then Ctrl+G C

```
man dvtm
```

Then you can learn how to use it.

Cool hey.

---

### Post by pythonscript on 2009-09-06
dvtm looks promising. Thank you!

---

### Post by pythonscript on 2009-09-07
Actually, twin is still looking like the nicest package, and it was in the repository for hardy, so I downloaded the deb from there. Is there a way for me to install this package on jaunty? dpkg returns: 
```
dpkg: dependency problems prevent configuration of twin:
 twin depends on libtw0 (>= 4.5.1-3); however:
  Package libtw0 is not installed.

```

Any ideas? I'd *really* like to get twin installed; it's looks like a nice package that I'd like to have, but if compiling from source doesn't work and neither does the repository... Did either my configure/make attachments from my first post make any sense to anyone? Thanks!

---

### Post by drhabber on 2010-08-21
> **pythonscript said:**
> 
Any ideas? I'd *really* like to get twin installed; it's looks like a nice package that I'd like to have, but if compiling from source doesn't work and neither does the repository... Did either my configure/make attachments from my first post make any sense to anyone? Thanks!

Did you find a way to run it with Ubuntu?

---

