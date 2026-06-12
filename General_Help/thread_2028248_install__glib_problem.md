---
title: "install  glib problem"
date: 2012-07-17
forum: General Help
---

### Post by luofeiyu on 2012-07-17
i have installed gettext  in  /opt/gtk&#65292;
 ./configure --prefix=/opt/gtk 
make
make install 
1.why pkg-config  --modversion  gettext can't find it?
root@ocean:~# pkg-config  --modversion  gettext
Package gettext was not found in the pkg-config search path.
Perhaps you should add the directory containing `gettext.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gettext' found

2.when i install glib&#65292;
./configure --prefix=/opt/gtk  
the output &#65292;  
checking for msgfmt... no  
configure: error:  
You must have either have gettext support in your C library, or use the  
GNU gettext library. ([http://www.gnu.org/software/gettext/gettext.html](http://www.gnu.org/software/gettext/gettext.html)  
how to solve it &#65311;

---

### Post by Paddy Landau on 2012-07-18
Why don't you just install [gettext]("apt:gettext") from the Ubuntu Software Centre? Then it will be in the proper path, and other applications will be able to find it.

---

