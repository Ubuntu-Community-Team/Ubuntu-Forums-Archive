---
title: "error compiling libfprint"
date: 2010-05-20
forum: General Help
---

### Post by mahendrakariya on 2010-05-20
Hi,

I downloaded the source code of libfprint anc configured it. When I tried to compile it, I got an error *glib/gstdio.h: No such file or directory*

Complete output of "make" is as follows.

```
root@PROXIMA:/home/mahendra/fprint/libfprint-0.1.0-pre2# make
make  all-recursive
make[1]: Entering directory `/home/mahendra/fprint/libfprint-0.1.0-pre2'
Making all in libfprint
make[2]: Entering directory `/home/mahendra/fprint/libfprint-0.1.0-pre2/libfprint'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -fvisibility=hidden -I./nbis/include -I/usr/include/libusb-1.0   -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include    -std=gnu99 -fgnu89-inline -Wall -Wundef -Wunused -Wstrict-prototypes -Werror-implicit-function-declaration -Wno-pointer-sign -Wshadow -fopenmp -I/usr/local/include/ImageMagick   -g -O2 -MT libfprint_la-data.lo -MD -MP -MF .deps/libfprint_la-data.Tpo -c -o libfprint_la-data.lo `test -f 'data.c' || echo './'`data.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -fvisibility=hidden -I./nbis/include -I/usr/include/libusb-1.0 -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -std=gnu99 -fgnu89-inline -Wall -Wundef -Wunused -Wstrict-prototypes -Werror-implicit-function-declaration -Wno-pointer-sign -Wshadow -fopenmp -I/usr/local/include/ImageMagick -g -O2 -MT libfprint_la-data.lo -MD -MP -MF .deps/libfprint_la-data.Tpo -c data.c  -fPIC -DPIC -o .libs/libfprint_la-data.o
data.c:29:25: error: glib/gstdio.h: No such file or directory
data.c: In function ‘storage_setup’:
data.c:63: error: implicit declaration of function ‘g_mkdir_with_parents’
data.c: In function ‘fp_print_data_save’:
data.c:257: error: implicit declaration of function ‘g_file_set_contents’
data.c: In function ‘fp_print_data_delete’:
data.c:375: error: implicit declaration of function ‘g_unlink’
data.c: In function ‘scan_dev_store_dir’:
data.c:490: error: implicit declaration of function ‘g_ascii_strtoull’
make[2]: *** [libfprint_la-data.lo] Error 1
make[2]: Leaving directory `/home/mahendra/fprint/libfprint-0.1.0-pre2/libfprint'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mahendra/fprint/libfprint-0.1.0-pre2'
make: *** [all] Error 2

```

Any workaround?

---

