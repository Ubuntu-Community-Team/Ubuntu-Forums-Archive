---
title: "amarok crashes"
date: 2010-04-26
forum: General Help
---

### Post by r_s on 2010-04-26
Earlier I had this problem that amarok never showed any lyrics although wiki and pictures for the artists were being shown, but today after some time amarok crashed , I ran gdb to find what was wrong and this is the output I got.


Loaded symbols for /usr/lib/libwbclient.so.0
Reading symbols from /lib/libcap.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/libcap.so.2
Reading symbols from /usr/lib/gconv/IBM850.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gconv/IBM850.so
Reading symbols from /usr/lib/xine/plugins/1.26/xineplug_decode_mad.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.26/xineplug_decode_mad.so
Reading symbols from /usr/lib/libmad.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libmad.so.0
Reading symbols from /usr/lib/kde4/amarok_context_applet_photos.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/kde4/amarok_context_applet_photos.so
Reading symbols from /usr/lib/kde4/amarok_data_engine_photos.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/kde4/amarok_data_engine_photos.so
0x00ef6422 in __kernel_vsyscall ()
(gdb) n
Single stepping until exit from function __kernel_vsyscall, 
which has no line number information.

Program received signal SIGCONT, Continued.
[Switching to Thread 0xb58f2b70 (LWP 14628)]
0x00ef6422 in __kernel_vsyscall ()


Any ideas ?
Or should it be reported as a bug?

---

