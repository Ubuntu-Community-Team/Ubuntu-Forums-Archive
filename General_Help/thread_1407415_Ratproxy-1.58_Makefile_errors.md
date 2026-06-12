---
title: "Ratproxy-1.58 Makefile errors"
date: 2010-02-15
forum: General Help
---

### Post by superdave16 on 2010-02-15
So im reading the metasploit unleashed documentation and in one section it teachs how to install and use ratproxy, and so i downloaded it extracted and patched the sources with ratproxy_wmap.diff in the metasploit installation. Unfortunately when i go to make it i get this:

root@Sitonmylap:/pentest/exploits/framework3/ratproxy# make
cc ratproxy.c -o ratproxy  -Wall -O3 -Wno-pointer-sign -D_GNU_SOURCE http.c mime.c ssl.c -lcrypto -lssl -lsqlite3
ratproxy.c:43:25: error: openssl/md5.h: No such file or directory
ratproxy.c: In function ‘save_trace’:
ratproxy.c:631: warning: passing argument 5 of ‘sqlite3_prepare’ from incompatible pointer type
/usr/include/sqlite3.h:2345: note: expected ‘const char **’ but argument is of type ‘_u8 **’
ratproxy.c: In function ‘decode_flash’:
ratproxy.c:738: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
http.c:43:25: error: openssl/md5.h: No such file or directory
http.c: In function ‘checksum_response’:
http.c:1345: error: ‘MD5_CTX’ undeclared (first use in this function)
http.c:1345: error: (Each undeclared identifier is reported only once
http.c:1345: error: for each function it appears in.)
http.c:1345: error: expected ‘;’ before ‘ctx’
http.c:1355: warning: implicit declaration of function ‘MD5_Init’
http.c:1355: error: ‘ctx’ undeclared (first use in this function)
http.c:1356: warning: implicit declaration of function ‘MD5_Update’
http.c:1357: warning: implicit declaration of function ‘MD5_Final’
http.c:1359: warning: dereferencing type-punned pointer will break strict-aliasing rules
mime.c:39:25: error: openssl/md5.h: No such file or directory
ssl.c:38:25: error: openssl/ssl.h: No such file or directory
ssl.c:39:25: error: openssl/err.h: No such file or directory
ssl.c: In function ‘ssl_start’:
ssl.c:107: error: ‘SSL_CTX’ undeclared (first use in this function)
ssl.c:107: error: (Each undeclared identifier is reported only once
ssl.c:107: error: for each function it appears in.)
ssl.c:107: error: ‘cli_ctx’ undeclared (first use in this function)
ssl.c:107: error: ‘srv_ctx’ undeclared (first use in this function)
ssl.c:107: warning: left-hand operand of comma expression has no effect
ssl.c:108: error: ‘SSL’ undeclared (first use in this function)
ssl.c:108: error: ‘cli_ssl’ undeclared (first use in this function)
ssl.c:108: error: ‘srv_ssl’ undeclared (first use in this function)
ssl.c:108: warning: left-hand operand of comma expression has no effect
ssl.c:109: error: ‘BIO’ undeclared (first use in this function)
ssl.c:109: error: ‘err’ undeclared (first use in this function)
ssl.c:137: warning: implicit declaration of function ‘SSL_library_init’
ssl.c:138: warning: implicit declaration of function ‘SSL_load_error_strings’
ssl.c:140: warning: implicit declaration of function ‘BIO_new_fp’
ssl.c:140: error: ‘BIO_NOCLOSE’ undeclared (first use in this function)
ssl.c:141: warning: implicit declaration of function ‘SSL_CTX_new’
ssl.c:141: warning: implicit declaration of function ‘SSLv23_client_method’
ssl.c:142: warning: implicit declaration of function ‘SSLv23_server_method’
ssl.c:144: warning: implicit declaration of function ‘ERR_print_errors’
ssl.c:146: warning: implicit declaration of function ‘SSL_CTX_use_certificate_chain_file’
ssl.c:149: warning: implicit declaration of function ‘SSL_CTX_use_PrivateKey_file’
ssl.c:149: error: ‘SSL_FILETYPE_PEM’ undeclared (first use in this function)
ssl.c:152: warning: implicit declaration of function ‘SSL_new’
ssl.c:157: warning: implicit declaration of function ‘SSL_set_fd’
ssl.c:158: warning: implicit declaration of function ‘SSL_connect’
ssl.c:162: warning: implicit declaration of function ‘SSL_accept’
ssl.c:190: warning: implicit declaration of function ‘SSL_read’
ssl.c:221: warning: implicit declaration of function ‘SSL_write’
make: *** [ratproxy] Error 1

---

### Post by kthari85 on 2010-06-24
Install libssl-dev :)

---

