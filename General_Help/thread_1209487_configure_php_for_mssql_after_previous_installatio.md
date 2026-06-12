---
title: "configure php for mssql after previous installation"
date: 2009-07-10
forum: General Help
---

### Post by Twallaroo on 2009-07-10
Hello all,

I have apache en php installed successfully on my server, but now I want to connect to a remote Microsoft SQL server.
When I try to do this with php, I get the error " PHP Fatal error:  Call to undefined function:  mssql_connect()"

I found that I didn't compile php with the option --with-mssql
So is it possible to just compile the mssql.so and add the extention in php.ini?

I don't want to uninstall and re-install php, because other production applications are using php.

According to phpinfo(), this is the used configure command:
```
'./configure' '--build=x86_64-redhat-linux-gnu' '--host=x86_64-redhat-linux-gnu'  '--target=x86_64-redhat-linux-gnu' '--program-prefix=' '--prefix=/usr'  '--exec-prefix=/usr' '--bindir=/usr/bin' '--sbindir=/usr/sbin'  '--sysconfdir=/etc' '--datadir=/usr/share' '--includedir=/usr/include'  '--libdir=/usr/lib64' '--libexecdir=/usr/libexec' '--localstatedir=/var'  '--sharedstatedir=/usr/com' '--mandir=/usr/share/man'  '--infodir=/usr/share/info' '--cache-file=../config.cache'  '--with-config-file-path=/etc' '--with-config-file-scan-dir=/etc/php.d'  '--enable-force-cgi-redirect' '--disable-debug' '--enable-pic' '--disable-rpath'  '--enable-inline-optimization' '--with-bz2' '--with-db4=/usr' '--with-curl'  '--with-exec-dir=/usr/bin' '--with-freetype-dir=/usr' '--with-png-dir=/usr'  '--with-gd=shared' '--enable-gd-native-ttf' '--without-gdbm' '--with-gettext'  '--with-ncurses=shared' '--with-gmp' '--with-iconv' '--with-jpeg-dir=/usr'  '--with-openssl' '--with-png' '--with-pspell' '--with-xml'  '--with-expat-dir=/usr' '--with-dom=shared,/usr' '--with-dom-xslt=/usr'  '--with-dom-exslt=/usr' '--with-xmlrpc=shared' '--with-pcre-regex=/usr'  '--with-zlib' '--with-layout=GNU' '--enable-bcmath' '--enable-exif'  '--enable-ftp' '--enable-magic-quotes' '--enable-sockets' '--enable-sysvsem'  '--enable-sysvshm' '--enable-track-vars' '--enable-trans-sid' '--enable-yp'  '--enable-wddx' '--with-pear=/usr/share/pear' '--with-imap=shared'  '--with-imap-ssl' '--with-kerberos' '--with-ldap=shared'  '--with-mysql=shared,/usr' '--with-pgsql=shared' '--with-snmp=shared,/usr'  '--with-snmp=shared' '--enable-ucd-snmp-hack' '--with-unixODBC=shared,/usr'  '--enable-memory-limit' '--enable-shmop' '--enable-calendar' '--enable-dbx'  '--enable-dio' '--enable-mbstring=shared' '--enable-mbstr-enc-trans'  '--enable-mbregex' '--with-mime-magic=/usr/share/file/magic.mime'  '--with-apxs2=/usr/sbin/apxs' 
```

I also have FreeTDS installed, if that could be usefull
Kind regards

---

### Post by Twallaroo on 2009-07-10
OK,

I installed php-mssql, and the mssql.so file was created.
So when I restart httpd, I see the following error in the messages:

```

PHP Warning:  Unknown(): Unable to load dynamic library '/usr/lib64/php4/mssql.so' - /usr/lib64/php4/mssql.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  Unknown(): Unable to load dynamic library '/usr/lib64/php4/mssql.so' - /usr/lib64/php4/mssql.so: cannot open shared object file: No such file or directory in Unknown on line 0
```

But the library is there:

```

root@host:/usr/lib64/php4> ls -la
total 188
drwxr-xr-x   2 root root  4096 Jul 10 16:56 .
drwxr-xr-x  93 root root 77824 Jul 10 04:02 ..
-rwxr-xr-x   1 root root 45632 Sep 12  2007 ldap.so
-rwxr-xr-x   1 root root 44136 Jul 10 16:56 mssql.so
root@bru0268x:/usr/lib64/php4> 
```

---

