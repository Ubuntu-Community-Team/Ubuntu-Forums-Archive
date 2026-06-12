---
title: "help on header files"
date: 2011-10-28
forum: General Help
---

### Post by just_abhi22 on 2011-10-28
hi
i want to compile my main program that required some header files.
i am not aware how to locate my header files i.e. how to give my linux its path for header files. please help me in doing so.
i had founded my required header files and placed them all in a directory along with my main file, still it gives error while compiling. why now?. it says " module.h: no such file or directory" even though that file is present in my directory.

how to connect header file folder to my programs??? 
my header files are located at "/usr/src/linux-headers-2.6.35-22/include/linux"

thank you

---

### Post by tors on 2011-10-28
The "-I" flag to "cc" specifies include directories.

#> man cc



Example:

main.cc
```

#include <stdio.h>

int main(void) {

    printf("Hello");

}
```

#> cc -I /usr/include/ main.cc

---

### Post by just_abhi22 on 2011-10-28
this does not solve my problem !!
i had tried copying all the required .h files in one directory and then compile but that doesn't worked. i had even copied the header files folder in "/usr/local/include" which is default location to be searched, but still it gives lot of errors.
i dont know how to compile a simple program requiring headers.
i had even tried "gcc -I /usr/src/kernels/2.6.18-262.el5-i686/include hello hello.c" but still could bot find out the way out....:confused:
please help me to add my header files to my program and compile it successfully.
thank you

---

### Post by deloquencia on 2011-10-28
Strange, usually the parameter -I should work.

You could try to provide absolute location, like that...

```

#include "/path/to/headers/headerfile.h"

int main(void) {

/*...*/

}


```

---

### Post by just_abhi22 on 2011-10-28
i am compiling this code

#include <linux/module.h> /* Needed by all modules */
#include <linux/kernel.h> /* Needed for KERN_INFO */
int init_module(void)
{
printk(KERN_INFO "Hello world 1.\n");
/*
* A non 0 return means init_module failed; module can't be loaded.
*/
return 0;
}
void cleanup_module(void)
{
printk(KERN_INFO "Goodbye world 1.\n");
}

and getting error as

abhi@ubuntu:/$ sudo gcc hello1.c
hello1.c:1: fatal error: linux/module.h: No such file or directory
compilation terminated.

some how "module.h" is not present at /usr /include or /usr/include/linux.......i think these are the places where linux would be searching for header files.

my all header files are located at "/usr/src/linux-headers-2.6.35-22/include"
now how to use all header files to compile my program??

please come up with genuine solution this time. i had already used "gcc -I /usr/src/....... hello1.c" but getting lot errors.....
thank you.

---

### Post by tors on 2011-10-28
What happens if you try this?

```
abhi@ubuntu:/$ gcc -I/usr/src/linux-headers-2.6.35-22/include hello1.c
```

---

### Post by deloquencia on 2011-10-28
I don't think you can compile anything kernel related like that. Check the options in the Makefiles how there gcc is used. 

It won't be that easy. I checked at my side your lines of code and **cc -I /usr/src/linux-headers-2.6.38-11/include/ mod.c -o mod** works, but there are another errors...

Check [http://kernelnewbies.org/KernelHeaders](http://kernelnewbies.org/KernelHeaders), like it's even recommended by the error output - headers and the kernel are not so trivial like a one-liner in c to handle.

By the way, what are you trying to code. Sorry - I don't want to be too offending, but check the kernel documentation first.

---

