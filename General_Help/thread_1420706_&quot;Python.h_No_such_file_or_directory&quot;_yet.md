---
title: "&quot;Python.h: No such file or directory&quot; yet I have installed python2.6-dev"
date: 2010-03-03
forum: General Help
---

### Post by pollo1 on 2010-03-03
I'm trying to extend Python with C but when I compile this message is displayed:

spammodule.c:1:20: error: Python.h: Nessun file o directory
spammodule.c:3: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
spammodule.c:15: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘SpamMethods’

I have already installed python2.6-dev and I have Python.h in the dyrectory /usr/include/python2.6/Python.h.

Can you help me?

Thanks.

---

### Post by sukhdeepsingh on 2010-06-16
I have the same problem and I think its occurring in UBUNTU 10.04 only.
```
ls /usr/include/python2.6/Python.h 
/usr/include/python2.6/Python.h

```


Please help

---

### Post by sukhdeepsingh on 2010-07-01
Hi,
I have found out the solution for this.
Though the python2.6-dev is installed, yet the compiler is not able to find it , because of path problem. I think they have changed it in new version of Ubuntu.

The simple solution is :

The header files are located in '/usr/include/' , such as <stdio.h>
So, what I did was i copied all the header files from '/usr/include/python2.6/' to '/usr/include/' and then compiled the program and it works.

Also , if it doesn't complies, try using c++ instead of cc or g++ instead of gcc.

I am not a Linux expert and can do research to get my work done.

Cheers to strugglers  

Sukhdeep Singh

---

