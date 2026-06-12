---
title: "help compiling source code"
date: 2010-11-05
forum: General Help
---

### Post by searchfgold6789 on 2010-11-05
Hi.
I was googling a 3D graphing calculator, and found one that might suit my needs, [_**FungCalc**_]("http://fung-calc.sourceforge.net/index.php"). I grabbed the source code and started following the instructions as listed:

>   1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes a while.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Type `make install' to install the programs and any data files and
     documentation.

  4. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  I CD'ed to the directory and typed ./configure, and it ran a file and made some files. There was some error that said checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

Then I typed make, and got an error:```
make: *** No targets specified and no makefile found.  Stop.
```What am I missing here??? Is there some other way to compile the program?
My objective is to install the program onto my computer.

---

### Post by VCoolio on 2010-11-05
You can't ignore ./configure errors and skip to 'make'. It checks for dependencies needed to 'make' which is where the actual work is done. Try to find out what the dependencies are (read the homepage of fungcalc or a README file or something. You'll need also the -dev packages for the dependencies. In this case I´d try if installing xorg-dev solves this particular error.

---

### Post by searchfgold6789 on 2010-11-05
I solved that by installing xorg-dev.
Now it has another dependency which is not clear to me: Qt4 libraries and headers.
The exact error:```
checking for Qt... configure: error: Qt (>= Qt 3.0) (headers and libraries) not found. Please check your installation!
```Which packages must I install??? There is not much info in the websites or doc's.

---

### Post by mc4man on 2010-11-05
I think at this point you're going to have a bit of trouble compiling this source which is fairly old.

Among other things you'll need qt3 headers (libqt3-headers, libqt3-mt-dev and need to point to in the ./configure, ie.
./configure --with-qt-includes=/usr/include/qt3
Then you'll run into the lack of mcopidl (libarts1-dev), last seen in intrepid.
While you can track down libarts1-dev, it's deps and install, other things may arise and even with a successful build may not run correctly, if at all

libarts-1-dev info
[https://launchpad.net/ubuntu/intrepid/+package/libarts1-dev](https://launchpad.net/ubuntu/intrepid/+package/libarts1-dev)

Ex. from above (32 bit - package and dep list
[https://launchpad.net/ubuntu/intrepid/i386/libarts1-dev/1.5.10-0ubuntu1](https://launchpad.net/ubuntu/intrepid/i386/libarts1-dev/1.5.10-0ubuntu1)

---

### Post by searchfgold6789 on 2010-11-05
I didn't plan on using more than 50 megabytes of disk space for the calculator.
So I removed everything and decided to use a different calculator.

---

