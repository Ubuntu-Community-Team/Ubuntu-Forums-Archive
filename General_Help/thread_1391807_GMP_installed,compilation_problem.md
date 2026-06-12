---
title: "GMP installed,compilation problem"
date: 2010-01-27
forum: General Help
---

### Post by kishorebjv on 2010-01-27
I have installed Gmp 5.0.0....

but when im trying to compile the code getting these errors!!!
the code as follows:
#include <stdio.h>
#include <gmp.h>

int  main (void)
     {
       mpz_t r, n;
       mpz_init (r);
       mpz_init_set_str (n, "123456", 0);
       gmp_printf ("%Zd\n", r);
       return 0;
     }
errors:
bvjkishore@ubuntu:~/c$ g++  k.cc  -lgmp
/lib/../lib/libgmp.so: undefined reference to `__gmpn_mul_1c'
/lib/../lib/libgmp.so: undefined reference to `__gmpn_rsh1add_n'
/lib/../lib/libgmp.so: undefined reference to `__gmpn_sub_nc'
/lib/../lib/libgmp.so: undefined reference to `__gmpn_modexact_1_odd'
/lib/../lib/libgmp.so: undefined reference to `__gmpn_add_nc'
/lib/../lib/libgmp.so: undefined reference to `__gmpn_addlsh1_n'
collect2: ld returned 1 exit status..

i have compiled like "g++  test.cc  -o test  -lgmp"

and the installation of gmp-5.0.0 is  done in asusal way ..like 
downloaded"gmp-5.0.0." from **gmp**lib.org/

and  unzip..with tar command

./configure
sudo  make all


please get me out of these problems!! ;(

---

### Post by lewisforlife on 2010-01-27
How are you compiling this program?  You have to link to the GMP library during compilation.  For example, if your file was test.c, you could do:

```
gcc -Wall test.c -o test -lgmp
```

---

### Post by lewisforlife on 2010-01-27
Oh, I see, you did show how you compiled it.  how did you install the GMP libraries, was it like this?

```
sudo apt-get install libgmp3-dev
```

You can check to see if it is installed by doing:

```
dpkg --get-selections | grep libgmp3-dev
```

Post the output of that, also try to compile using my above compile command and let me know the results.

---

### Post by kishorebjv on 2010-01-28
"bvjkishore@ubuntu:~$ sudo apt-get install libgmp3-dev""

Super command to get rid of this problem!!!


Thanks you sooooooooo much!!!:p:p:p
:popcorn:

---

