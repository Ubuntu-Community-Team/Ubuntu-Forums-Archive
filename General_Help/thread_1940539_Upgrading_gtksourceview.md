---
title: "Upgrading gtksourceview"
date: 2012-03-13
forum: General Help
---

### Post by steinkaare on 2012-03-13
For those of you who read my last thread I have now fixed the gtksource, all I needed was a good nights sleep. However a new problem occured. After I had installed all the packages correctly I ran the "./configure" command and it was sucsessfull, so the next step was the "make" command which resulted in two errors. This is what comes up in the terminal when I type "make check"  
```
kai@kai-laptop:~/Desktop/pspp-0.7.9$ make check
make  check-recursive
make[1]: Entering directory `/home/kai/Desktop/pspp-0.7.9'
Making check in gl
make[2]: Entering directory `/home/kai/Desktop/pspp-0.7.9/gl'
make  check-recursive
make[3]: Entering directory `/home/kai/Desktop/pspp-0.7.9/gl'
make[4]: Entering directory `/home/kai/Desktop/pspp-0.7.9/gl'
make[4]: Nothing to be done for `check-am'.
make[4]: Leaving directory `/home/kai/Desktop/pspp-0.7.9/gl'
make[3]: Leaving directory `/home/kai/Desktop/pspp-0.7.9/gl'
make[2]: Leaving directory `/home/kai/Desktop/pspp-0.7.9/gl'
Making check in po
make[2]: Entering directory `/home/kai/Desktop/pspp-0.7.9/po'
make[2]: Leaving directory `/home/kai/Desktop/pspp-0.7.9/po'
make[2]: Entering directory `/home/kai/Desktop/pspp-0.7.9'
/bin/bash ./libtool --tag=CC   --mode=link gcc -std=gnu99 -Wall -W -Wwrite-strings -Wstrict-prototypes -Wpointer-arith -Wno-sign-compare -Wmissing-prototypes -g -O2 -Wdeclaration-after-statement -fgnu89-inline     -o src/ui/terminal/pspp  src/ui/terminal/libui.la src/ui/libuicommon.la src/libpspp.la src/libpspp-core.la -pthread -L/usr/local/lib -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0   -L/usr/lib -lncurses -lreadline  -lgsl -lgslcblas -lz -lm  
libtool: link: gcc -std=gnu99 -Wall -W -Wwrite-strings -Wstrict-prototypes -Wpointer-arith -Wno-sign-compare -Wmissing-prototypes -g -O2 -Wdeclaration-after-statement -fgnu89-inline -o src/ui/terminal/.libs/pspp -pthread  src/ui/terminal/.libs/libui.a src/ui/.libs/libuicommon.a src/.libs/libpspp.so src/.libs/libpspp-core.so -L/usr/local/lib /usr/local/lib/libpangocairo-1.0.so /usr/local/lib/libpango-1.0.so /usr/lib/libcairo.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so /usr/lib/libgthread-2.0.so -lrt /usr/lib/libglib-2.0.so -L/usr/lib -lncurses -lreadline /usr/local/lib/libgsl.so /usr/local/lib/libgslcblas.so -lz -lm -pthread -Wl,-rpath -Wl,/usr/local/lib/pspp
src/.libs/libpspp.so: undefined reference to `gsl_cdf_beta_Pinv'
src/.libs/libpspp.so: undefined reference to `gsl_cdf_hypergeometric_P'
src/.libs/libpspp.so: undefined reference to `gsl_linalg_cholesky_invert'
src/.libs/libpspp.so: undefined reference to `gsl_cdf_poisson_P'
src/.libs/libpspp.so: undefined reference to `gsl_cdf_negative_binomial_P'
src/.libs/libpspp.so: undefined reference to `gsl_cdf_fdist_Pinv'
src/.libs/libpspp.so: undefined reference to `gsl_cdf_binomial_P'
src/.libs/libpspp.so: undefined reference to `gsl_cdf_geometric_P'
collect2: ld returned 1 exit status
make[2]: *** [src/ui/terminal/pspp] Error 1
make[2]: Leaving directory `/home/kai/Desktop/pspp-0.7.9'
make[1]: *** [check-recursive] Error 1
make[1]: Leaving directory `/home/kai/Desktop/pspp-0.7.9'
make: *** [check] Error 2

```
I am not very good at this, so I do not know what these errors mean and if the program can be installed anyway. I would appreciate some help. Thanks

---

### Post by steinkaare on 2012-03-14
Hi guys, I solved the previous problem, now I have a new one, it looks like the gsl package is not working correctly? btw im using ubuntu 10.04

---

