---
title: "python 3.1.1"
date: 2009-10-22
forum: General Help
---

### Post by bashphoenux on 2009-10-22
i downloaded python3.1.1 from the official website 
unrared it
configured it
and then typed 
make and at the end of it ... it showed me this:
```
INFO: Can't locate Tcl/Tk libs and/or headers

Python build finished, but the necessary bits to build these modules were not found:
_curses            _curses_panel      _dbm            
_gdbm              _hashlib           _sqlite3        
_ssl               _tkinter           bz2             
readline                                              
To find the necessary bits, look in setup.py in detect_modules() for the module's name.

```
what went wrong ?? what do i have to do? to get the make process to complete successfully ?

---

### Post by bashphoenux on 2009-10-22
anyone know wats wrong ??? please help me !!

---

### Post by Giblet5 on 2009-10-22
> **bashphoenux said:**
> i downloaded python3.1.1 from the official website 
unrared it
configured it
and then typed 
make and at the end of it ... it showed me this:
```
INFO: Can't locate Tcl/Tk libs and/or headers

Python build finished, but the necessary bits to build these modules were not found:
_curses            _curses_panel      _dbm            
_gdbm              _hashlib           _sqlite3        
_ssl               _tkinter           bz2             
readline                                              
To find the necessary bits, look in setup.py in detect_modules() for the module's name.

```
what went wrong ?? what do i have to do? to get the make process to complete successfully ?


The build process requires additional development libraries that you have not yet installed.

A real-quick search through synaptic tells me you need these packages and more... I got bored searching for them, so you finish up.

```
sudo apt-get install libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline5-dev
```


Also, if the python3 source came with a "configure" script, you should run that after you install the needed development libraries. That will re-create the Makefile to match your system.

Example:

```
make clean
./configure --prefix=/usr
make
```

---

### Post by bashphoenux on 2009-10-22
thanks alot !!! is there a command to download all the development libraries/packages ???

---

### Post by Giblet5 on 2009-10-22
> **bashphoenux said:**
> thanks alot !!! is there a command to download all the development libraries/packages ???

You DON'T want to do that just to build python. Trust me.

There are tens of thousands.

Just running the "./configure --prefix=/usr" script will tell you what development kits it would like to have but did not find installed. Those are clues, really...

"curses not found" tells me that the build can use the curses library and headers, but they're not installed. Curses is a generic term for 'terminal cursor control' that uses the terminfo data on thousands of different terminal devices. That's provided by the libncursesX-dev kit.

Searching in synaptic for "curses" shows me several to choose from. I'd select the one with the Ubuntu symbol next to it (it is blessed by the Ubuntu team).

After you install a kit, re-run the ./configure script! Fix any new missing packages.

Do that for python and you'll have most of what you need for many other source packages, but always use the configure script if one is provided.

---

### Post by bashphoenux on 2009-10-22
thanks once again !!!=D>
and above you would have noticed bz2 ... i cant find in synaptic package manager :(
there is bzip2,bzr ??
how do i identify which is the correct one ?and same goes for tkinter 
i just found Tk

---

### Post by Giblet5 on 2009-10-22
> **bashphoenux said:**
> thanks once again !!!=D>
and above you would have noticed bz2 ... i cant find in synaptic package manager :(
there is bzip2,bzr ??
how do i identify which is the correct one ?and same goes for tkinter 
i just found Tk

libbz2-dev

No, it wasn't obvious to me either.

This stuff's only a little easier when you're one of the people who wrote some of these kits.

I provide better hints in my autoconf (the tool that creates configure) scripts. though...

---

### Post by bashphoenux on 2009-10-22
thank you!! 
i just hope i get as good as you are some day !! :)

---

### Post by bashphoenux on 2009-10-22
A weird problem i am facing right now
```
Python build finished, but the necessary bits to build these modules were not found:
_sqlite3           _tkinter                           
To find the necessary bits, look in setup.py in detect_modules() for the module's name.

```

on typing sudo apt-get install sqlite3 
i get
```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
sqlite3 is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic libemeraldengine0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
on following your make clean and redoing the ./configure and make process i keep getting sqlite3 on that list what do i do now ?

---

### Post by bashphoenux on 2009-10-22
can someone please help me with this ???
every time i 'make'
i keep gettting
```

Python build finished, but the necessary bits to build these modules were not found:
_tkinter                                              
To find the necessary bits, look in setup.py in detect_modules() for the module's name.

``` what am i missing to install this tkinter ???on googling i got tcl/tk .. installed it but still problem persists !!!
what package/lib should i download to gete this tkinter working and my python 3 up and running ?

---

### Post by sirtrent on 2009-10-22
Did you try tkx.x-dev. You may need an older version of TK since I think python 3 is old. But there are several versions of tkx.x-dev in the repos.

---

### Post by bashphoenux on 2009-10-23
sorry i am actually trying to 'make' python 3.1.1
no luck with tkinter :(

---

