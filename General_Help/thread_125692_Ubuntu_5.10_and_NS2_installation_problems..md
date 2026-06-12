---
title: "Ubuntu 5.10 and NS2 installation problems."
date: 2006-02-04
forum: General Help
---

### Post by globemast on 2006-02-04
Hello guys,

i am a newbie to Ubuntu and Linux in general and i am trying to install NS2. (Network Simulator 2).

I have downloaded an executable installation version of NS2 and when i try to install it (by typing "./install") i get the following errors.

Can you please give me some help. Thanks in advance.

[COLOR="Blue"]
nicholas@hp-4152:~/Desktop/NS2/ns-allinone-2.26$ ./install
============================================================
* Testing for Cygwin environment
============================================================
Cygwin not detected, proceeding with regular install.
============================================================
* Build XGraph-12.1
============================================================
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... no
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking if malloc debugging is wanted... no
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.
./install: line 163: make: command not found
Can not create xgraph; But xgraph is an optional package, continuing...
============================================================
* Build CWeb
============================================================
Making cweb
./install: line 186: make: command not found
cweb failed to make, but it's optional
chmod: cannot access `cweave': No such file or directory
chmod: cannot access `ctangle': No such file or directory
ln: `cweave': File exists
ln: `ctangle': File exists
============================================================
* Build Stanford GraphBase
============================================================
Making sgb
./install: line 215: make: command not found
Unable to create sgb library, but it's optional, so continuing...
============================================================
* Build GT-ITM
============================================================
./install: line 246: make: command not found
./install: line 252: make: command not found
============================================================
* Build zlib
============================================================
Checking for gcc...
Building static library libz.a version 1.1.4 with gcc.
Checking for unistd.h... No.
Checking for errno.h...  No.
Checking for mmap support... No.
./install: line 272: make: command not found
Zlib make failed, but it's optional Continue ...
============================================================
* Build tcl8.3.2
============================================================
loading cache ./config.cache
checking for ranlib... ranlib
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.
tcl8.3.2 configuration failed! Exiting ...
Tcl is not part of the ns project.  Please see [www.Scriptics.com](www.Scriptics.com)
to see if they have a fix for your platform.[/COLOR]

---

### Post by lamego on 2006-02-04
The output shows you are missing "make" which is required to compile most of the software.
From a terminal  type:

```
sudo apt-get install make
```

---

### Post by globemast on 2006-02-04
I have installed make but i still get several problems. It says that the gcc compiler is not working.

I have the gcc compiler installed though.

---

### Post by globemast on 2006-02-04
Anyone can give a bit of help in this??

---

### Post by alt236 on 2006-02-18
Hi mate!

did you install the build-essentials?

```
sudo apt-get install build-essentials
```

also if I remember correctly, you need to install the X libraries (to compile xgraph, nam, tk and otcl):

```
sudo apt-get install xlibs-dev
```

---

### Post by alt236 on 2006-02-18
By the way, out of curiosity, why are you using ns2 2.26?

---

### Post by sundarece on 2006-02-28
[QUOTE=globemast]Anyone can give a bit of help in this??[/QUOTE]
I am going through almost the same thing here.
yes, the ns2.29 is available. I also initially had that error.. the header files were not there.. 
I installed the libdev6 (or something, I dont remember well) and gcc compiled normal .c files that I had, but the ./install still failed with this:

/home/sun/research/ns/ns-allinone-2.29/tk8.4.11/unix/../generic/tk3d.c:1301: err or: request for member ‘borderTable’ in something not a structure or union
/home/sun/research/ns/ns-allinone-2.29/tk8.4.11/unix/../generic/tk3d.c:1301: err or: request for member ‘borderTable’ in something not a structure or union
/home/sun/research/ns/ns-allinone-2.29/tk8.4.11/unix/../generic/tk3d.c:1305: err or: syntax error before ‘)’ token
/home/sun/research/ns/ns-allinone-2.29/tk8.4.11/unix/../generic/tk3d.c:1307: err or: syntax error before ‘)’ token
/home/sun/research/ns/ns-allinone-2.29/tk8.4.11/unix/../generic/tk3d.c:1307: err or: syntax error before ‘)’ token
/home/sun/research/ns/ns-allinone-2.29/tk8.4.11/unix/../generic/tk3d.c:1308: err or: syntax error before ‘)’ token
/home/sun/research/ns/ns-allinone-2.29/tk8.4.11/unix/../generic/tk3d.c: In funct ion ‘TkDebugBorder’:
/home/sun/research/ns/ns-allinone-2.29/tk8.4.11/unix/../generic/tk3d.c:1388: err or: ‘borderPtr’ undeclared (first use in this function)
/home/sun/research/ns/ns-allinone-2.29/tk8.4.11/unix/../generic/tk3d.c:1391: err or: invalid operands to binary *
/home/sun/research/ns/ns-allinone-2.29/tk8.4.11/unix/../generic/tk3d.c:1391: err or: syntax error before ‘)’ token
/home/sun/research/ns/ns-allinone-2.29/tk8.4.11/unix/../generic/tk3d.c:1394: err or: request for member ‘borderTable’ in something not a structure or union
/home/sun/research/ns/ns-allinone-2.29/tk8.4.11/unix/../generic/tk3d.c:1394: err or: request for member ‘borderTable’ in something not a structure or union
/home/sun/research/ns/ns-allinone-2.29/tk8.4.11/unix/../generic/tk3d.c:1396: err or: syntax error before ‘)’ token
{standard input}: Assembler messages:
{standard input}:13: Error: symbol `q' is already defined
{standard input}:25: Error: symbol `q' is already defined
{standard input}:31: Error: symbol `q' is already defined
{standard input}:37: Error: symbol `p' is already defined
{standard input}:79: Error: symbol `dy' is already defined
{standard input}:85: Error: symbol `dx' is already defined
make: *** [tk3d.o] Error 1
tk8.4.11 make failed! Exiting ...
For problems with Tcl/Tk see [http://www.scriptics.com](http://www.scriptics.com)


Does anyone have an idea of what is happening?

thanks.
Sundar

---

### Post by alt236 on 2006-02-28
Did you install xlibs-dev?

The errors you are getting mean that the x development libraries are not installed (don't ask me why it doesn't check beforehand or why the error mesage is not more descriptive....). It took me a while to figure that out when I was installing ns-2 2.29 a couple of weeks ago.

If xlibs-dev doesn't work, try xlibs-static-dev.

I *think* that i also installed gcc-3.3 when I was fighting to get it working but i'm not sure if it made any difference.

---

### Post by appleberry on 2006-04-03
Hi. I think I managed to install and validate ns-allinone-2.29 but now when I try to run a .tcl file, I get a message telling me that bash: ns: command not found. I think I've set the path for the environments correctly so what should I do?

---

### Post by alt236 on 2006-04-08
Sounds like a wrong path to me...

Type 'echo $PATH' in a command prompt (without the quotes :)) and see if the correct path to the ns-2 executable apears somewhere in the list.

I assume that, after the installation you entered the path the installer gave you in your .bash_rc file, right?

---

### Post by incognito07 on 2007-04-06
Hey alt236

I was having similar problems with the ns 2.31 build too. But after installing the xlibs-dev , things worked like magic and it successfully compiled. 

Thanks.

---

