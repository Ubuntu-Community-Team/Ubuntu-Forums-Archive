---
title: "Problems Installing pdftk 1.44 deb"
date: 2011-03-28
forum: General Help
---

### Post by dabbish on 2011-03-28
I'm trying to install pdftk 1.44 on Ubuntu 9.1 amd64. I tried compiling it but was unsuccessful. Then I tried installing this deb that I found:
[https://launchpad.net/ubuntu/+source/pdftk/1.44-1/+buildjob/2039198](https://launchpad.net/ubuntu/+source/pdftk/1.44-1/+buildjob/2039198)

But it gives me this error:

```
ubuntu@domU-12-31-39-0F-42-11:~$ sudo dpkg -i pdftk_1.44-1_amd64.deb 
Selecting previously deselected package pdftk.
(Reading database ... 36359 files and directories currently installed.)
Unpacking pdftk (from pdftk_1.44-1_amd64.deb) ...
dpkg: dependency problems prevent configuration of pdftk:
 pdftk depends on libgcj11 (>= 4.4); however:
  Package libgcj11 is not installed.
 pdftk depends on libgcj-bc (>= 4.5~); however:
  Version of libgcj-bc on system is 4.4.1-1ubuntu2.
dpkg: error processing pdftk (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 pdftk

```

When I try to install the dependencies that it complains about, I get this:

```
ubuntu@domU-12-31-39-0F-42-11:~$ sudo apt-get install libgcj11
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgcj11 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgcj11 has no installation candidate

```

And this:

```
ubuntu@domU-12-31-39-0F-42-11:~$ sudo apt-get install libgcj-bc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgcj-bc is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  pdftk: Depends: libgcj11 (>= 4.4) but it is not installable
         Depends: libgcj-bc (>= 4.5~) but 4.4.1-1ubuntu2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

I also tried 'apt-get -f install', but it didn't do anything.

---

### Post by vinan on 2011-04-28
have you tried to install from ubuntu software center ??

---

### Post by dabbish on 2011-04-28
No, I gave up and used another library.

---

