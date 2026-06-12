---
title: "Installing new version of pcman"
date: 2012-05-05
forum: General Help
---

### Post by Robbyx on 2012-05-05
The pcman web site [http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/) advises to do the following to install the beta version:

[I]Source code of libfm (required to compile pcmanfm):

git clone git://pcmanfm.git.sourceforge.net/gitroot/pcmanfm/libfm


Source code of new pcmanfm (This is a total re-write. If you need source code of old deprecated pcmanfm series, please check it out from svn repository.):

git clone git://pcmanfm.git.sourceforge.net/gitroot/pcmanfm/pcmanfm


Please install libfm before compiling pcmanfm. Libfm itself brings an standalone demo program named libfm-demo, which could work as a minimal file manager. Both libfm and pcmanfm can be compiled with following commands:

./configure --sysconfdir=/etc
make
sudo make install
[/I]

I have followed everything down to:
     ./configure --sysconfdir=/etc

When I run that line I get an error message:

robins@robin-EP35-DS3L:~$ ./config --sysconfdir=/etc
bash: ./config: No such file or directory
robins@robin-EP35-DS3L:~$ 

Could it be indicated how I can get that line to run?

Robin

---

### Post by Toz on 2012-05-12
> **Robbyx said:**
> The pcman web site [http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/) advises to do the following to install the beta version:

[I]Source code of libfm (required to compile pcmanfm):

git clone git://pcmanfm.git.sourceforge.net/gitroot/pcmanfm/libfm


Source code of new pcmanfm (This is a total re-write. If you need source code of old deprecated pcmanfm series, please check it out from svn repository.):

git clone git://pcmanfm.git.sourceforge.net/gitroot/pcmanfm/pcmanfm


Please install libfm before compiling pcmanfm. Libfm itself brings an standalone demo program named libfm-demo, which could work as a minimal file manager. Both libfm and pcmanfm can be compiled with following commands:

[COLOR="Red"]./configure [/COLOR]--sysconfdir=/etc
make
sudo make install
[/I]

I have followed everything down to:
     ./configure --sysconfdir=/etc

When I run that line I get an error message:

robins@robin-EP35-DS3L:~$ [COLOR="Red"]./config[/COLOR] --sysconfdir=/etc
bash: ./config: No such file or directory
robins@robin-EP35-DS3L:~$ 

Could it be indicated how I can get that line to run?

Robin
Make sure you run ./configure, not ./config.

---

