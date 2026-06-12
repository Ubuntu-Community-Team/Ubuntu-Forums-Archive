---
title: "Thunderbird 3.0 SEGV (in LDAP routine?)"
date: 2009-12-10
forum: General Help
---

### Post by dakine42 on 2009-12-10
Thunderbird 3.0 crashes with a SEGV on 64-bit Kubuntu using LDAP authentication. Stack trace from gdb shows:
#0  0x000000000045703e in free ()
#1  0x00007f51d94dbea4 in ldap_set_lderrno () from /usr/lib/thunderbird-3.0.1pre/libldap60.so
#2  0x00007f51d94f0884 in ldap_set_option () from /usr/lib/thunderbird-3.0.1pre/libldap60.so
#3  0x00007f51d04c3a46 in ?? () from /lib/libnss_ldap.so.2
#4  0x00007f51d04c463a in ?? () from /lib/libnss_ldap.so.2
#5  0x00007f51d04c4999 in ?? () from /lib/libnss_ldap.so.2
#6  0x00007f51d04c50b7 in _nss_ldap_getpwnam_r () from /lib/libnss_ldap.so.2
#7  0x00007f51d7cf9f4d in __getpwnam_r (name=0x7fff13664ab6 "hps", resbuf=0x7fff13662480, buffer=0x7f51d4136800 "ntp", buflen=1024,
    result=<value optimized out>) at ../nss/getXXbyYY_r.c:253
#8  0x00007f51db5ce95d in g_get_any_init_do () at /build/buildd/glib2.0-2.22.2/glib/gutils.c:1631
#9  0x00007f51db5cfe4d in g_get_any_init () at /build/buildd/glib2.0-2.22.2/glib/gutils.c:1782
#10 g_get_any_init_locked () at /build/buildd/glib2.0-2.22.2/glib/gutils.c:1789
#11 IA__g_get_user_name () at /build/buildd/glib2.0-2.22.2/glib/gutils.c:1807
#12 0x00007f51d3e964cd in gnome_client_instance_init (client=0x7f51d411d540) at gnome-client.c:1385
#13 0x00007f51dba58977 in IA__g_type_create_instance (type=<value optimized out>) at /build/buildd/glib2.0-2.22.2/gobject/gtype.c:1674
#14 0x00007f51dba3d7bc in g_object_constructor (type=2, n_construct_properties=89, construct_params=0x0)
    at /build/buildd/glib2.0-2.22.2/gobject/gobject.c:1383
#15 0x00007f51dba3e5dd in IA__g_object_newv (object_type=<value optimized out>, n_parameters=0, parameters=0x0)
    at /build/buildd/glib2.0-2.22.2/gobject/gobject.c:1171
#16 0x00007f51dba3f355 in IA__g_object_new_valist (object_type=139989427316768, first_property_name=0x0, var_args=0x7fff13662980)
    at /build/buildd/glib2.0-2.22.2/gobject/gobject.c:1323
#17 0x00007f51dba3f4ac in IA__g_object_new (object_type=139989427316768, first_property_name=0x0)
    at /build/buildd/glib2.0-2.22.2/gobject/gobject.c:1086
#18 0x00007f51d3e96252 in gnome_client_new_without_connection () at gnome-client.c:1512
#19 0x00007f51d3e97210 in gnome_client_pre_args_parse (app=<value optimized out>, mod_info=<value optimized out>) at gnome-client.c:1143
#20 0x00007f51d346af8e in gnome_program_preinit () from /usr/lib/libgnome-2.so.0
#21 0x00007f51d346d23c in ?? () from /usr/lib/libgnome-2.so.0
#22 0x00007f51d346d50d in gnome_program_initv () from /usr/lib/libgnome-2.so.0
#23 0x00007f51d346d60a in gnome_program_init () from /usr/lib/libgnome-2.so.0
#24 0x000000000044d242 in ?? ()
#25 0x0000000000447f3f in ?? ()
#26 0x0000000000445590 in ?? ()
#27 0x00007f51d7c75abd in __libc_start_main (main=<value optimized out>, argc=<value optimized out>, ubp_av=<value optimized out>,
    init=<value optimized out>, fini=<value optimized out>, rtld_fini=<value optimized out>, stack_end=0x7fff13663508) at libc-start.c:220
#28 0x0000000000445389 in ?? ()
#29 0x00007fff13663508 in ?? ()
#30 0x000000000000001c in ?? ()
#31 0x0000000000000001 in ?? ()
#32 0x00007fff13664624 in ?? ()
#33 0x0000000000000000 in ?? ()

I built a copy of the released source code, and it builds cleanly, but gives the same result.
Running the program in ddd, I found that at the crash point, the idalloc() function in $SRCDIR/mozilla/memory/jemalloc/jemalloc.c gets passed a pointer with a value of 0x2 from somewhere - I have not yet been able to track down where that comes from. So, I'm looking for some help, here! :confused:

Thanks!

---

### Post by dakine42 on 2009-12-14
Confirmed this problem is in the LDAP routines - I recompiled with --disable-ldap, and Thunderbird-3.0 (Shredder) works perfectly - except, of course, I don't have access to my LDAP directory.

---

