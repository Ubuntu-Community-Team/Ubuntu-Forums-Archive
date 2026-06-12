---
title: "make/compile issue with libgpod."
date: 2010-08-30
forum: General Help
---

### Post by guriinii on 2010-08-30
After installing iFuse, gtkpod and many dependencies, I've hit a problem far beyond my current understanding. Following this comment:[http://cgsbay.com/mount-iphone-ipod-touch-over-usb-in-linux/#comment-190]("http://cgsbay.com/mount-iphone-ipod-touch-over-usb-in-linux/#comment-190") everything was going well until I got this make error:
```
:~/libgpod$ make
make  all-recursive
make[1]: Entering directory `/home/greenys/libgpod'
Making all in src
make[2]: Entering directory `/home/greenys/libgpod/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/greenys/libgpod/src'
Making all in tools
make[2]: Entering directory `/home/greenys/libgpod/tools'
/bin/bash ../libtool --tag=CC   --mode=link gcc -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2   -I/usr/include/libxml2   -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I../src   -I/usr/include/libusb-1.0   -Wall     -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes     -Wnested-externs -Wpointer-arith     -Wcast-align -Wsign-compare     -Werror     -g -O0 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement   -o ipod-read-sysinfo-extended ipod_read_sysinfo_extended-read-sysinfoextended.o   ipod_read_sysinfo_extended-ipod-usb.o -lgobject-2.0 -lsqlite3 -lplist -lxml2 -lglib-2.0   -lxml2   -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -lglib-2.0   ../src/libgpod.la   -lusb-1.0   
libtool: link: gcc -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/include/libxml2 -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I../src -I/usr/include/libusb-1.0 -Wall -Wchar-subscripts -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wcast-align -Wsign-compare -Werror -g -O0 -Wno-strict-aliasing -Wno-sign-compare -Wdeclaration-after-statement -o .libs/ipod-read-sysinfo-extended ipod_read_sysinfo_extended-read-sysinfoextended.o ipod_read_sysinfo_extended-ipod-usb.o  ../src/.libs/libgpod.so /usr/lib/libsqlite3.so -ldl -lpthread -lplist /usr/lib/libxml2.so /usr/lib/libgdk_pixbuf-2.0.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so /usr/lib/libglib-2.0.so -lz -lm /usr/lib/libusb-1.0.so -lrt -pthread
/usr/local/lib/libgio-2.0.so.0: undefined reference to `g_ptr_array_new_with_free_func'
/usr/local/lib/libgio-2.0.so.0: undefined reference to `g_error_new_valist'
/usr/local/lib/libgio-2.0.so.0: undefined reference to `g_realloc_n'
/usr/local/lib/libgio-2.0.so.0: undefined reference to `g_hostname_is_non_ascii'
/usr/local/lib/libgio-2.0.so.0: undefined reference to `g_malloc0_n'
/usr/local/lib/libgio-2.0.so.0: undefined reference to `g_hostname_to_ascii'
/usr/local/lib/libgio-2.0.so.0: undefined reference to `g_mkstemp_full'
/usr/local/lib/libgio-2.0.so.0: undefined reference to `g_array_get_type'
/usr/local/lib/libgio-2.0.so.0: undefined reference to `g_byte_array_unref'
/usr/local/lib/libgio-2.0.so.0: undefined reference to `g_byte_array_get_type'
/usr/local/lib/libgio-2.0.so.0: undefined reference to `g_malloc_n'
/usr/local/lib/libgio-2.0.so.0: undefined reference to `g_main_context_get_thread_default'
collect2: ld returned 1 exit status
make[2]: *** [ipod-read-sysinfo-extended] Error 1
make[2]: Leaving directory `/home/greenys/libgpod/tools'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/greenys/libgpod'
make: *** [all] Error 2
``` 
Can anyone please advise?

---

