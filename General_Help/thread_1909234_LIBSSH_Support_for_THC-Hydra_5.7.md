---
title: "LIBSSH Support for THC-Hydra 5.7"
date: 2012-01-14
forum: General Help
---

### Post by marpis on 2012-01-14
Hi guys, sorry to ask for help on my first post but i've been struggling with the ssh module for days..

I have the libssh-dev and libssh-2-1-dev installed and they get found during the configuring phase but when i actually try to use the module i get : > Error: Compiled without LIBSSH v0.4.x support, module is not available!
my ./configure is:


```

Starting hydra auto configuration ...
Detected 32 Bit Linux OS

Checking for openssl (libssl, libcrypto, ssl.h, sha.h) ...
                                                       ... found
Checking for idn (libidn.so) ...
                             ... found
Checking for pcre (libpcre.so, pcre.h) ...
                                       ... found
Checking for Postgres (libpq.so, libpq-fe.h) ...
                                             ... found
Checking for SVN (libsvn_client-1 libapr-1.so libaprutil-1.so) ...
                                                               ... found
Checking for firebird (libfbclient.so) ...
                                       ... found
Checking for MYSQL client (libmysqlclient.so, math.h) ...
                                                      ... found
Checking for AFP (libafpclient.so) ...
                                   ... NOT found, module Apple Filing Protocol disabled - Apple sucks anyway
Checking for NCP (libncp.so / nwcalls.h) ...
                                         ... found
Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from [http://www.sap.com/solutions/netweaver/linux/eval/index.asp](http://www.sap.com/solutions/netweaver/linux/eval/index.asp)
Checking for libssh (libssh/libssh.h) ...
                                      ... found
Checking for Oracle (libocci.so libclntsh.so / oci.h) ...
                                                      ... NOT found, module Oracle disabled
Checking for GUI req's (pkg-config, gtk+-2.0) ...
                                              ... found

Hydra will be installed into .../bin of: /home/marpis/hydra2/h
  (change this by running ./configure --prefix=path)

Writing Makefile.in ...
now type "make"
```and the compilation data i get is : 

```
[marpis@marpis-ubuntu:~/hydra2$ make
gcc -I. -O3 -o pw-inspector  pw-inspector.c
gcc -I. -O3 -c hydra-vnc.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-pcnfs.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-rexec.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-nntp.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-socks5.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-telnet.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-cisco.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-http.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-ftp.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-imap.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-pop3.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-smb.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-icq.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-cisco-enable.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-ldap.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-mysql.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-mssql.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-xmpp.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-http-proxy-urlenum.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-snmp.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-cvs.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-smtp.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-smtp-enum.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-sapr3.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-ssh.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-teamspeak.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-postgres.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-rsh.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-rlogin.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-oracle-listener.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-svn.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-pcanywhere.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-sip.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-oracle-sid.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-oracle.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-vmauthd.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-firebird.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-afp.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-ncp.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-http-proxy.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-http-form.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-irc.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-rdp.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c crc32.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c d3des.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c bfg.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c ntlm.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c sasl.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hmacmd5.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -c hydra-mod.c -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H -I/usr/include/subversion-1 -I/usr/include/apr-1.0 -I/usr/include/subversion-1 -I/usr/include/mysql
gcc -I. -O3 -lm -o hydra  hydra.c hydra-vnc.o hydra-pcnfs.o hydra-rexec.o hydra-nntp.o hydra-socks5.o hydra-telnet.o hydra-cisco.o hydra-http.o hydra-ftp.o hydra-imap.o hydra-pop3.o hydra-smb.o hydra-icq.o hydra-cisco-enable.o hydra-ldap.o hydra-mysql.o hydra-mssql.o hydra-xmpp.o hydra-http-proxy-urlenum.o hydra-snmp.o hydra-cvs.o hydra-smtp.o hydra-smtp-enum.o hydra-sapr3.o hydra-ssh.o hydra-teamspeak.o hydra-postgres.o hydra-rsh.o hydra-rlogin.o hydra-oracle-listener.o hydra-svn.o hydra-pcanywhere.o hydra-sip.o hydra-oracle-sid.o hydra-oracle.o hydra-vmauthd.o hydra-firebird.o hydra-afp.o hydra-ncp.o hydra-http-proxy.o hydra-http-form.o hydra-irc.o hydra-rdp.o crc32.o d3des.o bfg.o ntlm.o sasl.o hmacmd5.o hydra-mod.o -lm -lssl -lncp -lfbclient -lidn -lpcre -lmysqlclient -lpq -lsvn_client-1 -lapr-1 -laprutil-1 -lsvn_subr-1 -lssh -lcrypto -L/usr/lib -L/usr/local/lib -L/lib -L/lib/i386-linux-gnu -L/usr/lib/i386-linux-gnu -L/usr/lib -DLIBOPENSSL -DLIBOPENSSLNEW -DLIBFIREBIRD -DLIBIDN -DHAVE_PR29_H -DHAVE_PCRE -DLIBMYSQLCLIENT -DLIBNCP -DLIBPOSTGRES -DLIBSVN -DLIBSSH -DHAVE_MATH_H
```

cd hydra-gtk && sh ./make_xhydra.sh
Trying to compile xhydra now (hydra gtk gui) - dont worry if this fails, this is really optional ...
sudo ma`src/xhydra' -> `../xhydra'
The GTK GUI is ready, type "./xhydra" to start

Now type make install
marpis@marpis-ubuntu:~/hydra2$ sudo make install
[sudo] password for marpis: 
strip hydra pw-inspector
echo OK > /dev/null && test -x xhydra && strip xhydra || echo OK > /dev/null
mkdir -p /home/marpis/hydra2/h/bin 
cp hydra pw-inspector dpl4hydra* /home/marpis/hydra2/h/bin && cd /home/marpis/hydra2/h/bin && chmod 755 hydra pw-inspector
echo OK > /dev/null && test -x xhydra && cp xhydra /home/marpis/hydra2/h/bin && cd /home/marpis/hydra2/h/bin && chmod 755 xhydra || echo OK > /dev/null
mkdir -p /home/marpis/hydra2/h/man/man1
cp -f hydra.1 xhydra.1 pw-inspector.1 /home/marpis/hydra2/h/man/man1 

any ideas?

---

### Post by howefield on 2012-01-14
Post spliced off to its own thread. You'll probably get better help that way.

---

### Post by marpis on 2012-01-15
Thank you! BTW the version of hydra im trying to get to work is 7.1 but i can't manage to change the thread title :D

hope somebody can help :(

---

### Post by marpis on 2012-01-16
nobody had this problem? :(

---

### Post by marpis on 2012-01-22
anybody at least know where i can check where hydra expects to find the libraries?

---

