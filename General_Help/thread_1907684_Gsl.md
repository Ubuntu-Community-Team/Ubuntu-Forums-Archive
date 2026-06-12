---
title: "Gsl"
date: 2012-01-11
forum: General Help
---

### Post by davoudi on 2012-01-11
Hi everybody,

 So I recently installed gsl library using sudo apt-get install libgsl0-dev.

 I use a simple example 
> 
     #include <stdio.h>
     #include <gsl/gsl_rng.h>
     #include <gsl/gsl_randist.h>
     
     int
     main (void)
     {
       const gsl_rng_type * T;
       gsl_rng * r;
     
       int i, n = 10;
       double mu = 3.0;
     
       /* create a generator chosen by the 
          environment variable GSL_RNG_TYPE */
     
       gsl_rng_env_setup();
     
       T = gsl_rng_default;
       r = gsl_rng_alloc (T);
     
       /* print n random variates chosen from 
          the poisson distribution with mean 
          parameter mu */
     
       for (i = 0; i < n; i++) 
         {
           unsigned int k = gsl_ran_poisson (r, mu);
           printf (" %u", k);
         }
     
       printf ("\n");
       gsl_rng_free (r);
       return 0;
     }



 and using g++ -o exe_file -lgsl file.cpp
but I get the following errors
> 
A.cpp:(.text+0x1e): undefined reference to `gsl_rng_env_setup'
A.cpp:(.text+0x25): undefined reference to `gsl_rng_default'
A.cpp:(.text+0x35): undefined reference to `gsl_rng_alloc'
A.cpp:(.text+0x53): undefined reference to `gsl_ran_poisson'
A.cpp:(.text+0x91): undefined reference to `gsl_rng_free'

Any help is appreciated.

---

### Post by davoudi on 2012-01-15
By the way I am using Ubuntu 11.10.

---

### Post by 196sigma on 2012-01-27
Having the same issue on 11.10. Any help would be much appreciated.

---

### Post by 196sigma on 2012-01-27
Actually just found the solution.
Basically, you have to put the compiler flags in the correct order. That is, after the compile statement:

```
$ gcc temp.c -o temp -lgsl -lgslcblas
```

Background:
<a href="http://askubuntu.com/questions/71623/why-does-gsl-library-not-compile-link-in-11-10-despite-that-it-did-under-11-04">http://askubuntu.com/questions/71623/why-does-gsl-library-not-compile-link-in-11-10-despite-that-it-did-under-11-04</a>

and
<a href="http://ubuntuforums.org/archive/index.php/t-1833136.html">http://ubuntuforums.org/archive/index.php/t-1833136.html</a>

HTH

---

