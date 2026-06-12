---
title: "how do I know which compilers have been installed on a machine?"
date: 2012-04-29
forum: General Help
---

### Post by subjugater on 2012-04-29
I am now using a public cluster which I've never used before and wondering which fortran compiler is there. Is there a terminal command can tell me which compilers have been installed?

Thanks!!!

---

### Post by Alan.Brown on 2012-04-29
Most installations (if not all) will have **GCC** - **GNU Compiler Collection**.  See
**[http://en.wikipedia.org/wiki/GNU_Compiler_Collection](http://en.wikipedia.org/wiki/GNU_Compiler_Collection)**.

This includes the front end for **FORTRAN**.

To check if **GCC** is installed enter **gcc --version** in a terminal.   You should get the version number.

Hope this helps.

Alan

---

### Post by forrestcupp on 2012-04-29
Usually a default install doesn't include compilers. You have to install the build-essentials package to get all of that. It doesn't include those things to keep people who don't know what they're doing from messing things up.

```
sudo apt-get install build-essentials
```

---

### Post by Alan.Brown on 2012-04-30
**build-essentials**
> If you do not plan to build Debian packages, you don't need this
package.  Starting with dpkg (>= 1.14.18) this package is required
for building Debian packages.

This package contains an informational list of packages which are
considered essential for building Debian packages.  This package also
depends on the packages on that list, to make it easy to have the
build-essential packages installed.


This is not relevant to knowing whether the FORTRAN compiler is present in an installation.

Alan

---

### Post by forrestcupp on 2012-04-30
> **Alan.Brown said:**
> **build-essentials**


This is not relevant to knowing whether the FORTRAN compiler is present in an installation.

Alan

They must have changed things, then. At one time, you didn't get GCC at all without build-essential. Sorry about the mix up.

---

### Post by Alan.Brown on 2012-04-30
Thats OK

In my installation - Xubuntu 12.04 and Ubuntu 12.04 - I have **gcc** but not **build-essentials.**

As you say things have changed.

Alan

---

