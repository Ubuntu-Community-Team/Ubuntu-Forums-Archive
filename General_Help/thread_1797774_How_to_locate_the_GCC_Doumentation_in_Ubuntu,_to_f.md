---
title: "How to locate the GCC Doumentation in Ubuntu?, to find out the numeric value of EOF"
date: 2011-07-05
forum: General Help
---

### Post by varunaub on 2011-07-05
I installed GCC(GNU Compiler Collection) using apt-get install, including everything.I don't know where to accesses the GCC Documentation in Linux in particular the Header file<stdio.h>. I wan to find out the numeric value for EOF in Linux.:confused:

---

### Post by dino99 on 2011-07-05
open synaptic and search: gcc-4.6-doc (not installed by default)

[http://superuser.com/questions/119387/using-gcc-documentation](http://superuser.com/questions/119387/using-gcc-documentation)

You can use dpkg to know more about gcc-4.6-doc after installing it
$ dpkg -s gcc-4.6-doc

---

### Post by varunaub on 2011-07-05
I have installed the gcc-doc But I am not able to locate where it is.I want to know How to access it

---

### Post by Bachstelze on 2011-07-05
```

#include <stdio.h>

int main(void)
{
    printf("%d\n", EOF);
    return 0;
}
```

Or [font=monospace]grep EOF /usr/include/stdio.h[/font].  Note that the value of EOF is implementation-dependent, so you should not rely on it having any specific value.  It is, however, guaranteed to be a negative value of type int.

---

### Post by vivek.pandey on 2011-07-05
any documentation about any installed package can be found here /usr/share/doc

plus man package also helps
like man gcc   or
man iverilog 
etc

---

