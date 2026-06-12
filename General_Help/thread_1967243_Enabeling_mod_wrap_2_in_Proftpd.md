---
title: "Enabeling mod_wrap_2 in Proftpd"
date: 2012-04-27
forum: General Help
---

### Post by relli10 on 2012-04-27
Hi all,

Im a long time reader but 1st time poster. Recently I have been getting a large number of ftp (and ssh) connections requests from Asian countries on my personal FTP server. I discovered the package called blockhosts ([link]("http://www.aczoom.com/blockhosts")) which I have configured to use with my ssh server and it is doing the trick in limiting these rouge connections. However Im yet to get it working in proftpd.

My reading has shown that I need to configure proftpd with the "mod_wrap_2" ([link]("http://www.proftpd.org/docs/contrib/mod_wrap2.html")) module to enable proftpd to use tcp_wrappers as blockhosts relies on host.allow to block unwanted connections.

Im running Ubuntu lycid Lynx 10.04LTS with proftpd 1.3.2c. When I type:

```
proftpd -V 
```Output shows that the proftpd was compiled with mod_wrap_2:

```
... Built With:
    configure  '--prefix=/usr' '--with-includes=/usr/include/postgresql:/usr/include/mysql' '--mandir=/usr/share/man' '--sysconfdir=/etc/proftpd' '--localstatedir=/var/run' '--libexecdir=/usr/lib/proftpd' '--enable-sendfile' '--enable-facl' '--enable-dso' '--enable-autoshadow' '--enable-ctrls' '--with-modules=mod_readme' '--enable-ipv6' '--enable-nls' '--build' 'i486-linux-gnu' '--with-shared=mod_unique_id:mod_site_misc:mod_load:mod_ban:mod_quotatab:mod_sql:mod_sql_mysql:mod_sql_postgres:mod_sql_sqlite:mod_sql_odbc:mod_dynmasq:mod_quotatab_sql:mod_ldap:mod_quotatab_ldap:mod_ratio:mod_tls:mod_rewrite:mod_radius:mod_wrap:mod_wrap2:mod_wrap2_file:mod_wrap2_sql:mod_quotatab_file:mod_quotatab_radius:mod_facl:mod_ctrls_admin:mod_ifsession' 'build_alias=i486-linux-gnu' 'CFLAGS=-O2 -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -DHAVE_OPENSSL -DUSE_LDAP_TLS ' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS=' 'CXXFLAGS=-g -O2' 'FFLAGS=-g -O2' ... 
```However when I ```
proftpd -l
```The output doesn not list mod_wrap_2 as compiled:

```
Compiled-in modules:
  mod_core.c
  mod_xfer.c
  mod_auth_unix.c
  mod_auth_file.c
  mod_auth.c
  mod_ls.c
  mod_log.c
  mod_site.c
  mod_delay.c
  mod_facts.c
  mod_dso.c
  mod_ident.c
  mod_auth_pam.c
  mod_readme.c
  mod_cap.c
  mod_ctrls.c
  mod_lang.c
```I then added ```
<IfModule mod_wrap2_file.c>
    WrapEngine on
    WrapTables file:/etc/hosts.allow file:/etc/hosts.deny
    WrapLog /var/proftpd/wrap2.log
</IfModule>
``` to my proftpd.conf file but proftpd was still ignoreing /etc/hosts.allow and would not write any log file

Can anybody give me some direction on how to configure proftpd to use mod_wrap_2? 

I really want to be able to stop all of these connections attempts.

Thanks

---

