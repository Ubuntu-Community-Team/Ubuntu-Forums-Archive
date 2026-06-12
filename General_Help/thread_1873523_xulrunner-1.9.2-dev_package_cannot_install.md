---
title: "xulrunner-1.9.2-dev package cannot install"
date: 2011-11-01
forum: General Help
---

### Post by fidogenial on 2011-11-01
Hi All,

 I'm trying to install  xulrunner-1.9.2-dev package but if i run
sudo get-apt install  xulrunner-1.9.2-dev  it say package is obsolete or it is available from another source.

since xulrunner is not present in my system i'm get following error while running some other application

../../bin/gcc/libgpac.so: undefined reference to  `JS_GC'
../../bin/gcc/libgpac.so: undefined reference to  `JS_ConvertStub'
../../bin/gcc/libgpac.so: undefined reference to  `JS_LookupProperty'
../../bin/gcc/libgpac.so: undefined reference to  `JS_AddValueRoot'


so how can i install the xulrunner-1.9.2-dev in my system

thanks
fido

---

### Post by polki@mac.com on 2011-11-03
I'm also interested in getting xulrunner installed on my 11.10 Ubuntu. Without it the internal browser in a bookkeeping application written in Java doesn't work.

---

### Post by shyamalapati on 2012-01-10
> **polki@mac.com said:**
> I'm also interested in getting xulrunner installed on my 11.10 Ubuntu. Without it the internal browser in a bookkeeping application written in Java doesn't work.

i downloaded and installed it from 

[http://mirror.pnl.gov/ubuntu//pool/universe/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.17+build3+nobinonly-0ubuntu1_i386.deb](http://mirror.pnl.gov/ubuntu//pool/universe/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.17+build3+nobinonly-0ubuntu1_i386.deb)

and it worked for me.

---

### Post by raja.genupula on 2012-01-10
Hi get the package from ubuntu packages (do google with ubuntu package xulrunner-1.9.2-dev ) and download it. 

sudo dpkg -i <placefilename>.deb

or use synaptic to find and install.

all the best.

---

