---
title: "Evolution Crash on Startup"
date: 2009-09-21
forum: General Help
---

### Post by PerfectReign on 2009-09-21
I had evolution working at one point.

I hadn't tried it in some months. I just launched it and it went away. I tried from the command line and got a whole host of errors. Googling gave me too much to digest. Any ideas from those who might have experienced this?




[FONT=System][COLOR=Blue]
kai@r2d2:~$ evolution
** (evolution:14628): DEBUG: Loading Exchange MAPI Plugin 

** (evolution:14628): DEBUG: MAPI listener is constructed with 0 listed MAPI accounts 
  
  
  
  
  
  
  
  
  
  
  
  
*** glibc detected *** evolution: realloc(): invalid pointer: 0xb5a77a00 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6925604]
/lib/tls/i686/cmov/libc.so.6(realloc+0x242)[0xb692a022]
/lib/libnss_wins.so.2(Realloc+0xc3)[0xb4d248cd]
/lib/libnss_wins.so.2(realloc_array+0x6a)[0xb4d249c0]
/lib/libnss_wins.so.2(debug_add_class+0x7b)[0xb4d0bf50]
/lib/libnss_wins.so.2(debug_init+0x3b)[0xb4d0c0a4]
/lib/libnss_wins.so.2(setup_logging+0x26)[0xb4d0ce37]
/lib/libnss_wins.so.2(_nss_wins_gethostbyname_r+0xf3)[0xb4c2070e]
/lib/libnss_wins.so.2(_nss_wins_gethostbyname2_r+0x4f)[0xb4c20ca3]
/lib/tls/i686/cmov/libc.so.6[0xb697e23a]
/lib/tls/i686/cmov/libc.so.6(getaddrinfo+0x1bf)[0xb697fc7f]
/usr/lib/libldap_r-2.4.so.2(ldap_connect_to_host+0x249)[0xb4e65fe9]
/usr/lib/libldap_r-2.4.so.2(ldap_int_open_connection+0x7a)[0xb4e4ceca]
/usr/lib/libldap_r-2.4.so.2(ldap_new_connection+0x210)[0xb4e63230]
/usr/lib/libldap_r-2.4.so.2(ldap_open_defconn+0x41)[0xb4e4ce21]
/usr/lib/libldap_r-2.4.so.2(ldap_send_initial_request+0x103)[0xb4e63e93]
/usr/lib/libldap_r-2.4.so.2(ldap_ntlm_bind+0x12b)[0xb4e7a48b]
/usr/lib/libexchange-storage-1.2.so.3[0xb4f34aa4]
/usr/lib/libexchange-storage-1.2.so.3[0xb4f34fa1]
/usr/lib/libexchange-storage-1.2.so.3[0xb4f3514f]
/usr/lib/libexchange-storage-1.2.so.3(e2k_global_catalog_lookup+0x222)[0xb4f35f72]
/usr/lib/libexchange-storage-1.2.so.3(exchange_account_connect+0x60c)[0xb4f22a7c]
/usr/lib/evolution/2.26/plugins/liborg-gnome-exchange-operations.so(exchange_config_listener_authenticate+0x11e)[0xb518744e]
/usr/lib/evolution/2.26/plugins/liborg-gnome-exchange-operations.so[0xb51884f5]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__OBJECT+0x8c)[0xb6ae88ac]
/usr/lib/libgobject-2.0.so.0[0xb6ada3d9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab)[0xb6adbc7b]
/usr/lib/libgobject-2.0.so.0[0xb6af1aff]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7b9)[0xb6af34b9]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb6af3936]
/usr/lib/libedataserver-1.2.so.11[0xb77539ab]
/usr/lib/libedataserver-1.2.so.11(e_account_list_construct+0x141)[0xb7753be1]
/usr/lib/evolution/2.26/plugins/liborg-gnome-exchange-operations.so[0xb5187086]
/usr/lib/libglib-2.0.so.0[0xb6a50c81]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8)[0xb6a52b88]
/usr/lib/libglib-2.0.so.0[0xb6a560eb]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0xb6a565ba]
/usr/lib/libbonobo-2.so.0(bonobo_main+0x63)[0xb743dcc3]
evolution[0x805d563]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb68cc775]
evolution[0x8050221]
======= Memory map: ========
08048000-08064000 r-xp 00000000 08:01 3047765    /usr/bin/evolution
08064000-08065000 r--p 0001b000 08:01 3047765    /usr/bin/evolution
08065000-08067000 rw-p 0001c000 08:01 3047765    /usr/bin/evolution
09866000-099f2000 rw-p 09866000 00:00 0          [heap]
b4be7000-b4df9000 r-xp 00000000 08:01 3556640    /lib/libnss_wins.so.2
b4df9000-b4dfa000 ---p 00212000 08:01 3556640    /lib/libnss_wins.so.2
b4dfa000-b4dfe000 r--p 00212000 08:01 3556640    /lib/libnss_wins.so.2
b4dfe000-b4e03000 rw-p 00216000 08:01 3556640    /lib/libnss_wins.so.2
b4e03000-b4e04000 rw-p b4e03000 00:00 0 
b4e1a000-b4e30000 r-xp 00000000 08:01 3048967    /usr/lib/libsasl2.so.2.0.22
b4e30000-b4e31000 r--p 00015000 08:01 3048967    /usr/lib/libsasl2.so.2.0.22
b4e31000-b4e32000 rw-p 00016000 08:01 3048967    /usr/lib/libsasl2.so.2.0.22
b4e32000-b4e3e000 r-xp 00000000 08:01 3049613    /usr/lib/liblber-2.4.so.2.4.1
b4e3e000-b4e3f000 r--p 0000b000 08:01 3049613    /usr/lib/liblber-2.4.so.2.4.1
b4e3f000-b4e40000 rw-p 0000c000 08:01 3049613    /usr/lib/liblber-2.4.so.2.4.1
b4e40000-b4e80000 r-xp 00000000 08:01 3049618    /usr/lib/libldap_r-2.4.so.2.4.1
b4e80000-b4e81000 ---p 00040000 08:01 3049618    /usr/lib/libldap_r-2.4.so.2.4.1
b4e81000-b4e82000 r--p 00040000 08:01 3049618    /usr/lib/libldap_r-2.4.so.2.4.1
b4e82000-b4e83000 rw-p 00041000 08:01 3049618    /usr/lib/libldap_r-2.4.so.2.4.1
b4e83000-b4e84000 rw-p b4e83000 00:00 0 
b4e84000-b4e8c000 r-xp 00000000 08:01 3072417    /usr/lib/evolution/2.26/libevolution-addressbook-importers.so.0.0.0
b4e8c000-b4e8d000 ---p 00008000 08:01 3072417    /usr/lib/evolution/2.26/libevolution-addressbook-importers.so.0.0.0
b4e8d000-b4e8e000 r--p 00008000 08:01 3072417    /usr/lib/evolution/2.26/libevolution-addressbook-importers.so.0.0.0
b4e8e000-b4e8f000 rw-p 00009000 08:01 3072417    /usr/lib/evolution/2.26/libevolution-addressbook-importers.so.0.0.0
b4e8f000-b4e93000 r-xp 00000000 08:01 3072416    /usr/lib/evolution/2.26/libevolution-addressbook-a11y.so.0.0.0
b4e93000-b4e94000 r--p 00003000 08:01 3072416    /usr/lib/evolution/2.26/libevolution-addressbook-a11y.so.0.0.0
b4e94000-b4e95000 rw-p 00004000 08:01 3072416    /usr/lib/evolution/2.26/libevolution-addressbook-a11y.so.0.0.0
b4e95000-b4e9e000 r-xp 00000000 08:01 3072469    /usr/lib/evolution/2.26/libevolution-smime.so.0.0.0
b4e9e000-b4e9f000 r--p 00008000 08:01 3072469    /usr/lib/evolution/2.26/libevolution-smime.so.0.0.0
b4e9f000-b4ea0000 rw-p 00009000 08:01 3072469    /usr/lib/evolution/2.26/libevolution-smime.so.0.0.0
b4ea0000-b4eab000 r-xp 00000000 08:01Aborted
kai@r2d2:~$ [/COLOR][/FONT]

---

### Post by PerfectReign on 2009-09-21
Okay, I went home from work and tried again after a reboot. This time, evolution loads. 

It took about 30 seconds from clicking the link to actually seeing a GUI. 

Apparently I had a similar question earlier this year - [http://ubuntuforums.org/showthread.php?p=7639914](http://ubuntuforums.org/showthread.php?p=7639914)


I had gotten Evolution working once in a while, but not consistently. 

Any ideas?


 [http://www.perfectreign.com/stuff/2009/20090527_evolution.jpg](http://www.perfectreign.com/stuff/2009/20090527_evolution.jpg)

<edit>
Apparently I also had this issue on openSUSE..  [http://www.nabble.com/Evolution-Dying-td19908235.html](http://www.nabble.com/Evolution-Dying-td19908235.html)

Bummer!
</edit>

---

