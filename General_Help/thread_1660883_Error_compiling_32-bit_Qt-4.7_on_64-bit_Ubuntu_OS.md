---
title: "Error compiling 32-bit Qt-4.7 on 64-bit Ubuntu OS"
date: 2011-01-06
forum: General Help
---

### Post by royalibrahim on 2011-01-06
Hi,

I am compiling Qt-4.7 for 32-bit on 64-bit (x86_64) Ubuntu 8.04 desktop.  I have installed all the 32-bit libraries (/lib32 and /usr/lib32)  through **getlibs** and "**apt-get install ia32-libs**". But I am getting the following error while configuring the qt project as:
  
```
./configure -platform linux-g++-32
```

 [COLOR=Red]Error: /usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.4/libstdc++.so when searching for -lstdc++[/COLOR]

It seems, the compiler still searching the libstdc++ in the 64 bit lib path inspite of the configuration argument for 32-bit.

Please let me know how to overcome this error 		   		  		  		  		  		  		 			 []("http://www.unix.com/editpost.php?do=editpost&p=302485681")

---

