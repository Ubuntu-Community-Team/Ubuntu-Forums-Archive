---
title: "Where is make?"
date: 2011-08-23
forum: General Help
---

### Post by bkejser on 2011-08-23
Hi

How do I install "make" using apt-get? I can't determine the name of the package that contains "make".

Thanks

---

### Post by LemursDontExist on 2011-08-23
You should find it in the 'build-essential' package.

```
sudo apt-get install build-essential
```

---

### Post by bkejser on 2011-08-23
Hi

When I run that command, the error "Unable to locate package build-essential" is returned.

This is a fresh install of ubuntu server 11.

Thanks

---

### Post by papibe on 2011-08-23
As far as I know it is in the make package:
```
$ dpkg -L make
/.
/usr
/usr/bin
**/usr/bin/make**
/usr/share
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/make.1.gz
/usr/share/doc
/usr/share/doc/make
/usr/share/doc/make/changelog.Debian.gz
/usr/share/doc/make/changelog.gz
/usr/share/doc/make/NEWS.gz
/usr/share/doc/make/NEWS.Debian.gz
/usr/share/doc/make/copyright
/usr/share/doc/make/README.gz
/usr/share/doc/make/Explanations.gz
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/make
```
It is usually installed. If not, you can do this:
```
$ sudo apt-get update
$ sudo apt-get install make
```Regards.

---

### Post by LemursDontExist on 2011-08-23
> **bkejser said:**
> Hi

When I run that command, the error "Unable to locate package build-essential" is returned.

This is a fresh install of ubuntu server 11.

Thanks

Try running 
```
sudo apt-get update
```
to make sure you've got an up to date package list.

Also try
```
apt-cache search build-essential
```
and see what turns up.

Finally, check
```
ls /usr/bin/make
```
to see if it's not already installed!

As papibe pointed out - it's also in the 'make' package - 'build-essential' contains all the core utilities for building code, so it's good to have, but you should try just installing 'make' to be sure.

Let us know the output if those commands!

---

