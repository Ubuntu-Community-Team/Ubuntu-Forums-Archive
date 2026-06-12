---
title: "Little issue with the drivers"
date: 2011-08-29
forum: General Help
---

### Post by freefixkorma on 2011-08-29
hi guys i am running ubuntu 10.4 desktop edition on a dell desktop i bought a new printer a Canon Pixma MP250 i am trying to install it but it send me to choose the model and everything but does not appear on the list so i chose the recommend there and nothing the printer is idle for ever ,the last printer i had an hp it will install automatically with not problem , i have the drivers cd that came with printer is anything i can do with that will appreciate any guidance and how to thanks 


freefix

---

### Post by wormyblackburny on 2011-08-29
[http://support-au.canon.com.au/P/search?model=PIXMA+MP250&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-au.canon.com.au/P/search?model=PIXMA+MP250&menu=download&filter=0&tagname=g_os&g_os=Linux)

You will want the debian package. Just download and double click and it should install.....

---

### Post by freefixkorma on 2011-08-29
thanks for the help it is a tar. file how do i execute it dont know how to do it will appreciate thanks in advance and i sorry for my stupidity and ignorance 

thanks 

freefix

---

### Post by freefixkorma on 2011-08-29
thank you sir i got it done thanks for your patience 

freefix

---

### Post by garvinrick4 on 2011-08-29
# 1: Uncompress tarball

To uncompress them, execute the following command(s) depending on the extension:
$ tar zxf file.tar.gz
$ tar zxf file.tgz
$ tar jxf file.tar.bz2
$ tar jxf file.tbz2

Now change directory
$ ls
$ cd path-to-software/

# 2: Build and install software

Generally you need to type 3 commands as follows for building and compiling software:
# ./configure
# make
# make install

Where,

    ./configure will configure the software to ensure your system has the necessary functionality and libraries to successfully compile the package
    make will compile all the source files into executable binaries.
    Finally, make install will install the binaries and any supporting files into the appropriate locations.

# 3: Read INSTALL / README file

Each tarball comes with installation and build instructions. Open INSTALL or README file for more information:

---

