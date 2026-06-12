---
title: "ngspice installation problems"
date: 2009-10-07
forum: General Help
---

### Post by locombian on 2009-10-07
Hi

Im having trouble installing ngspice. I read the thread:

 [http://ubuntuforums.org/archive/index.php/t-292856.html](http://ubuntuforums.org/archive/index.php/t-292856.html)

this is very old,  and I havent found anything up to date regarding this software.

after i download the package '[COLOR=Red]ngspice_17.0.0-1_i386.deb[/COLOR]' and type in the terminal '[COLOR=Red]sudo dpkg -i ngspice_17.0.0-1_i386.deb[/COLOR]'  i get  broken packages installed and i have to go to  synaptic to get rid of them.

any suggestions?

Thanks

---

### Post by lsm542 on 2009-10-18
> **locombian said:**
> Hi

Im having trouble installing ngspice. I read the thread:

 [http://ubuntuforums.org/archive/index.php/t-292856.html](http://ubuntuforums.org/archive/index.php/t-292856.html)

this is very old,  and I havent found anything up to date regarding this software.

after i download the package '[COLOR=Red]ngspice_17.0.0-1_i386.deb[/COLOR]' and type in the terminal '[COLOR=Red]sudo dpkg -i ngspice_17.0.0-1_i386.deb[/COLOR]'  i get  broken packages installed and i have to go to  synaptic to get rid of them.

any suggestions?

Thanks


I'm not very experienced with linux, but I was able to successfully install ng-spice-rework-18 on Ubuntu 8.04 by making sure all the components needed were installed:

bison,flex,X11,autocinf,automake,libtool,textinfo

All of these elements are supported by Ubuntu, but the X11 component needed was libx11-dev.  This component is evidently not installed as part of the standard Ubuntu package.   This X11 component was necessary to get the post processor graphing to work, when specifying the "xgraph" option:

$ ./configure --enable-xgraph

Have fun....

PS  I'm using ngspice with easy_spice

---

