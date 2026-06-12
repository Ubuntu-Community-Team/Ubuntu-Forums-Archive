---
title: "Command perl Makefile.PL; not finding Makefile.PL"
date: 2006-04-03
forum: General Help
---

### Post by Ben Stamper on 2006-04-03
> 
~$ perl Makefile.PL
Can't open perl script "Makefile.PL": No such file or directory

Trying to compile GTKPod following these instructions:
> 
sudo apt-get install libexpat1-dev libglade2-0 libglade2-dev flex libid3tag0 libid3tag0-dev
wget [http://search.cpan.org/CPAN/authors/id/M/MS/MSERGEANT/XML-Parser-2.34.tar.gz](http://search.cpan.org/CPAN/authors/id/M/MS/MSERGEANT/XML-Parser-2.34.tar.gz)
tar xzf XML-Parser-2.34.tar.gz
perl Makefile.PL
make
sudo checkinstall -D make install
wget [http://umn.dl.sourceforge.net/sourceforge/gtkpod/libgpod-0.3.2.tar.gz](http://umn.dl.sourceforge.net/sourceforge/gtkpod/libgpod-0.3.2.tar.gz)
tar xzf libgpod-0.3.2.tar.gz
cd libgpod-0.3.2/
./configure
make
sudo checkinstall -D make install
sudo cp /usr/local/lib/libgpod* /usr/lib
wget [http://easynews.dl.sourceforge.net/sourceforge/gtkpod/gtkpod-0.99.4.tar.gz](http://easynews.dl.sourceforge.net/sourceforge/gtkpod/gtkpod-0.99.4.tar.gz)
tar xzf gtkpod-0.99.4.tar.gz
cd gtkpod-0.99.4
./configure
make
sudo checkinstall -D make install

All the modules seem to be loaded, anyone know what's causing this?

---

### Post by lcg on 2006-04-03
[QUOTE=Ben Stamper]Trying to compile GTKPod following these instructions:
```
...
wget http://search.cpan.org/CPAN/authors/...er-2.34.tar.gz
tar xzf XML-Parser-2.34.tar.gz
perl Makefile.PL
make
...
```
All the modules seem to be loaded, anyone know what's causing this?[/QUOTE]
When you extract XML-Parser, it creates a directory 'XML-Parser-2.34'. Did you 'cd' into that dir before 'perl Makefile.PL'?

HTH,
Lars

---

### Post by Fleaman13 on 2006-04-08
bash: make: command not found

this is what I get... do I have to cd to somewhere else to have the make command work? (still learning the commands, sorry if this is a dumb question)

---

### Post by llamakc on 2006-04-08
type in the console/Terminal:

which make

does it show /usr/bin/make ?

If not, install make.

sudo apt-get install make

---

### Post by x5452 on 2006-04-11
im following that same how to, i cd into the xml-parser directory, i can then perl Makefile.PL, then it does stuff, then i type make, it does more stuff, then i try sudo checkinstall -D make install and i keep getting:

sudo:  checkinstall:  command not found

whats that about?

---

### Post by llamakc on 2006-04-11
Anytime you are compiling from source and a library or development header or binary is not found, and the script barfs out and tells you, do an:

apt-cache search name-of-program

ken@vulva:~$ apt-cache search checkinstall
checkinstall - installation tracker

and of course the next gives you info:

ken@vulva:~$ apt-cache show checkinstall
Package: checkinstall
Priority: optional
Section: universe/admin
Installed-Size: 132
Maintainer: Matt Hope <dopey@debian.org>
Architecture: all
Version: 1.5.3-3ubuntu1
Depends: installwatch (>> 0.6), file, make
Filename: pool/universe/c/checkinstall/checkinstall_1.5.3-3ubuntu1_all.deb
Size: 35004

So a simple `sudo apt-get install checkinstall` would put that package on my machine for me.

As for Perl packages, you can also search for those with apt:

ken@vulva:~$ apt-cache search xml-parser
libxml-parser-perl - Perl module for parsing XML files

In Debian-based distros, perl module packages are named in the above fashion. 

HTH. (Try the Debian one before using cpan or something you downloaded unless you have version-specific needs)

---

