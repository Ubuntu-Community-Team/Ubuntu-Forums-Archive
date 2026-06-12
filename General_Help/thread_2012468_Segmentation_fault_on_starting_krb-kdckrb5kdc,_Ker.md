---
title: "Segmentation fault on starting krb-kdc/krb5kdc, Kerberos set up with LDAP backend"
date: 2012-06-29
forum: General Help
---

### Post by ilungi on 2012-06-29
Hello all.

Not sure if this is the right place to post this question, since I'm new, therefore please move to the appropriate section.

I installed Kerberos with LDAP backend, was working on the installation following a couple of guides, had populated the LDAP backend, had almost everything in place except the final testing. Prior to this, point, as far as I know, everythign was working fine, even starting the kadmin/kdc services. But now I'm getting a segfault on launching the service. Below, I've copied the error from my syslog -

```
Jun 29 15:12:02 k1 kernel: [2971837.133606] krb5kdc[3369]: segfault at 4 ip 00007fba76e4b7ae sp 00007fff9a093f20 error 4 in libkdb5.so.6.0[7fba76e43000+10000]

```

I'm running Ubuntu 12.04 x64, all updates have been applied, etc., and so far the only other problem I have had was with using GNUTLS with LDAP (which was fixed by editing the config in LDAP). Google has been my friend thus far, but this time I have not had any luck on finding a fix. My krb5.conf file is also pretty standard, and I'm posting the config file as well as additional info in case someone is facing/has faced a similar issue. 

Thanks in advance.

Sami

```
root@k1:# cat /etc/krb5.conf 
[libdefaults]
   default_realm = bitxtiger.NET

[realms]
bitxtiger.NET = {
   default_domain = bitxtiger.net
   kdc = k1.bitxtiger.net:88
   admin_server = k1.bitxtiger.net:750
   database_module = openldap_ldapconf
}

[domain_realm]
   .bitxtiger.net = bitxtiger.NET
   bitxtiger.net = bitxtiger.NET

[dbdefaults]
   ldap_kerberos_container_dn = ou=krb5,dc=bitxtiger,dc=net

[dbmodules]
   openldap_ldapconf = {
      db_library = kldap
      ldap_kdc_dn = cn=kdcsvc,ou=krb5,dc=bitxtiger,dc=net
      ldap_kadmind_dn = cn=kadmin,ou=krb5,dc=bitxtiger,dc=net
      ldap_service_password_file = /etc/krb5kdc/service.keyfile
      ldap_servers = ldap://k1.bitxtiger.net
      ldap_conns_per_server = 3
   }

[logging]
   default = FILE:/var/log/kerberos/klib.log
   kdc = FILE:/var/log/kerberos/kdc.log
   admin_server = FILE:/var/log/kerberos/kadmin.log

```   

```
root@k1:# ltrace /usr/sbin/krb5kdc
__libc_start_main(0x405810, 1, 0x7fffeba9b438, 0x4183b0, 0x418440 <unfinished ...>
setlocale(5, "")                                                     = "en_US.UTF-8"
strrchr("/usr/sbin/krb5kdc", '/')                                    = "/krb5kdc"
malloc(256)                                                          = 0x02121f20
krb5int_init_context_kdc(0x7fffeba9b308, 131312, 0x2121f20, 0, 3)    = 0
krb5_klog_init(0x2122120, 0x419e40, 0x7fffeba9b940, 1, 0x2122898)    = 0
malloc(16)                                                           = 0x02122690
krb5_aprof_init(0x419d55, 0x419d44, 0x7fffeba9b200, 0x7f76f2c56728, 0x21226f0) = 0
krb5_aprof_get_string(0x2123e00, 0x7fffeba9b1c0, 1, 0x7fffeba9b1f0, 0x7f76f3763e28) = 0
krb5_aprof_get_string(0x2123e00, 0x7fffeba9b1c0, 1, 0x7fffeba9b1f8, 0x2122898) = 0xffffffffaaca6003
krb5_aprof_get_int32(0x2123e00, 0x7fffeba9b1c0, 1, 0x61e9a0, 0x2122898) = 0xaaca6003
krb5_aprof_get_boolean(0x2123e00, 0x7fffeba9b1c0, 1, 0x7fffeba9b21c, 0x2122898) = 0xaaca6003
krb5_aprof_get_string_all(0x2123e00, 0x7fffeba9b1c0, 0x7fffeba9b208, 0x7f76f2c56748, 0x2122898) = 0xaaca6003
krb5_aprof_get_string_all(0x2123e00, 0x7fffeba9b1c0, 0x7fffeba9b210, 0x7f76f2c56748, 0x2122898) = 0xaaca6003
krb5_aprof_finish(0x2123e00, 0xffffffff, 0, 0x7f76f2c56748, 0x2122898) = 0
calloc(1, 1)                                                         = 0x02123e50
getopt(1, 0x7fffeba9b438, "x:r:d:mM:k:R:e:P:p:s:nw:4:X3")            = -1
krb5_get_default_realm(0x2122120, 0x7fffeba9b1e8, 0x7f76f2c56258, 0, 0) = 0
malloc(144)                                                          = 0x02122c30
__strdup(0x2122b00, 0x2122b00, 0, 0, 0x2122700)                      = 0x2122ae0
krb5int_init_context_kdc(0x2122c38, 0x2122b0e, 0, 0x54454e2e524547, 0x2123e60) = 0
krb5_read_realm_params(0x21249e0, 0x2122ae0, 0x7fffeba9b130, 75, 0x2122898) = 0
malloc(4)                                                            = 0x02122b70
__strdup(0x2123d40, 0x7f76f2c56720, 0x7f76f2c56720, 0x7f76f2c56728, 0x2123fc0) = 0x2123fd0
__strdup(0x2123e50, 0x2123d47, 0, 0x38382c, 0x2123fa0)               = 0x2123fb0
__strdup(0x2123db0, 0x2123e51, 0, 0, 0x2123fe0)                      = 0x2123ff0
krb5_free_realm_params(0x21249e0, 0x2123ec0, 604800, 0x646b3562726b2f63, 0x68736174732f63) = 0
krb5_set_default_realm(0x21249e0, 0x2122b00, 0, 0x7f76f2c56750, 0x68736174732f63) = 0
krb5_db_open(0x21249e0, 0, 256, 0x54454e2e524547, 0x2123d30)         = 0
krb5_db_setup_mkey_name(0x21249e0, 0x2122b70, 0x2122ae0, 0, 0x2122c70) = 0
krb5_db_fetch_mkey(0x21249e0, 0x213ae40, 16, 0, 0)                   = 0
krb5_db_fetch_mkey_list(0x21249e0, 0x213ae40, 0x2122c78, 1, 0x2122c90 <unfinished ...>
--- SIGSEGV (Segmentation fault) ---
+++ killed by SIGSEGV +++

```

```
root@k1:# ldd /usr/sbin/krb5kdc
        linux-vdso.so.1 =>  (0x00007fff6bfd7000)
        libkadm5srv_mit.so.8 => /usr/lib/x86_64-linux-gnu/libkadm5srv_mit.so.8 (0x00007f11cada9000)
        libkdb5.so.6 => /usr/lib/x86_64-linux-gnu/libkdb5.so.6 (0x00007f11cab98000)
        libgssrpc.so.4 => /usr/lib/x86_64-linux-gnu/libgssrpc.so.4 (0x00007f11ca97b000)
        libkrb5.so.3 => /usr/lib/x86_64-linux-gnu/libkrb5.so.3 (0x00007f11ca6ad000)
        libk5crypto.so.3 => /usr/lib/x86_64-linux-gnu/libk5crypto.so.3 (0x00007f11ca485000)
        libcom_err.so.2 => /lib/x86_64-linux-gnu/libcom_err.so.2 (0x00007f11ca280000)
        libkrb5support.so.0 => /usr/lib/x86_64-linux-gnu/libkrb5support.so.0 (0x00007f11ca078000)
        libverto.so.1 => /usr/lib/x86_64-linux-gnu/libverto.so.1 (0x00007f11c9e73000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f11c9ab5000)
        libgssapi_krb5.so.2 => /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2 (0x00007f11c9877000)
        libkeyutils.so.1 => /lib/x86_64-linux-gnu/libkeyutils.so.1 (0x00007f11c9673000)
        libresolv.so.2 => /lib/x86_64-linux-gnu/libresolv.so.2 (0x00007f11c9456000)
        libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f11c9239000)
        /lib64/ld-linux-x86-64.so.2 (0x00007f11cafd6000)
        libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f11c9035000)

```

---

### Post by ilungi on 2012-07-09
Still stuck. Anyone with any suggestions/input on this? Thanks.

---

### Post by knomegnome on 2013-02-06
Old thread, but I had this same trouble :) In fact, exactly the same.

Turns out its related to a bug in libkbd5 when using LDAP as a back end, and the krbPrincipalKey is NULL, most likely.

What I did the first time I encountered this issue was:

- Followed the Ubuntu OpenLDAP guide and The Kerberos/LDAP guide carefully
- Realized there was no guideline as to how to setup an LDAP Consumer for use by a secondary kdc, so put in the kerberos schema AND created the realm on the LDAP secondary before setting up the Consumer
- followed by segfaults

I wiped the secondary slapd using apt-get purge, rebuilt according to the guidelines, and did NOT create the realm but DID import the kerberos schema, and then configured the consumer

Worked like a charm. Replication brought over all the kerberos attributes and I didn't need to create the realm on the LDAP consumer.

---

