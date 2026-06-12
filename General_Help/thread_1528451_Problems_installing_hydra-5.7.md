---
title: "Problems installing hydra-5.7"
date: 2010-07-10
forum: General Help
---

### Post by radiostorm on 2010-07-10
Okay so I'm trying to install "hydra-5.7" from a .tar.gz file, ./configure works, but when I type "make" I get the following output: 

gcc -I. -Wall -O2 -lm -o hydra hydra-vnc.o hydra-pcnfs.o hydra-rexec.o hydra-nntp.o hydra-socks5.o hydra-telnet.o hydra-cisco.o hydra-http.o hydra-ftp.o hydra-imap.o hydra-pop3.o hydra-smb.o hydra-icq.o hydra-cisco-enable.o hydra-ldap.o hydra-mysql.o hydra-http-proxy.o hydra-smbnt.o hydra-mssql.o hydra-snmp.o hydra-cvs.o hydra-smtpauth.o hydra-sapr3.o hydra-ssh2.o hydra-teamspeak.o hydra-postgres.o hydra-rsh.o hydra-rlogin.o hydra-oracle-listener.o hydra-svn.o hydra-pcanywhere.o hydra-sip.o hydra-vmauthd.o hydra-smtpauth-ntlm.o hydra-firebird.o hydra-ncp.o hydra-http-proxy-auth-ntlm.o hydra-imap-ntlm.o hydra-pop3-ntlm.o hydra-http-form.o crc32.o d3des.o md4.o hydra-mod.o ntlm.o hydra.o -lm -lpq -L/usr/lib -L/usr/local/lib -L/lib -L/usr/lib
/usr/bin/ld: cannot find -lpq
collect2: ld returned 1 exit status
make: *** [hydra] Error 1

So I searched "-lpq" and got absolutely nothing. I'm fairly new to Ubuntu, so I am probably missing something ridiculously obvious. So please be kind D:
If anyone can point me in the right direction, it would be appreciated :)

---

### Post by farkinid on 2010-08-18
I'm having the same exact problem.

I've got all my dependencies installed.

---

### Post by silbak04 on 2010-08-19
Do you have OpenSSL, because you need OpenSSL to compile Hydra...after  that, try running ```
make 
make install 
```

---

### Post by silbak04 on 2010-08-19
Try this: ```
sudo aptitude install build-essential
```

---

### Post by silbak04 on 2010-08-19
```
cd /into/where/you/extracted/hydra
./configure
make
make install
```if you still have errors read me the output

---

### Post by farkinid on 2010-08-19
Ok guys, I've gotten past the -lpq problem with some major google-fu.

To get past it do the following :-

[LIST]
[*]Type 'make clean' while in your build directory
[*]Type './configure'
[*]gedit Makefile
[*]delete the entrees '-DLIBPOSTGRES' and '-lpq' which should be on the 3rd and 4th line respectively
[*]Save the file and run make
[/LIST]
Now onwards to my problem. After running make, I'm getting the following error

```
gcc -I. -Wall -O2 -lm -o hydra hydra-vnc.o hydra-pcnfs.o hydra-rexec.o hydra-nntp.o hydra-socks5.o hydra-telnet.o hydra-cisco.o hydra-http.o hydra-ftp.o hydra-imap.o hydra-pop3.o hydra-smb.o hydra-icq.o hydra-cisco-enable.o hydra-ldap.o hydra-mysql.o hydra-http-proxy.o hydra-smbnt.o hydra-mssql.o hydra-snmp.o hydra-cvs.o hydra-smtpauth.o hydra-sapr3.o hydra-ssh2.o hydra-teamspeak.o hydra-postgres.o hydra-rsh.o hydra-rlogin.o hydra-oracle-listener.o hydra-svn.o hydra-pcanywhere.o hydra-sip.o hydra-vmauthd.o hydra-smtpauth-ntlm.o hydra-firebird.o hydra-ncp.o hydra-http-proxy-auth-ntlm.o hydra-imap-ntlm.o hydra-pop3-ntlm.o hydra-http-form.o crc32.o d3des.o md4.o hydra-mod.o ntlm.o hydra.o -lm -lssl -lssh -lcrypto -L/usr/lib -L/usr/local/lib -L/lib -L/lib -L/usr/lib
hydra-ssh2.o: In function `start_ssh2':
hydra-ssh2.c:(.text+0x257): undefined reference to `ssh_options_set'
hydra-ssh2.c:(.text+0x270): undefined reference to `ssh_options_set'
hydra-ssh2.c:(.text+0x28f): undefined reference to `ssh_options_set'
hydra-ssh2.c:(.text+0x2ac): undefined reference to `ssh_options_set'
hydra-ssh2.c:(.text+0x2c9): undefined reference to `ssh_options_set'
collect2: ld returned 1 exit status
make: *** [hydra] Error 1

```

Looks like a code error in hydra-ssh2.c but I'm no expert programmer. Any ideas?

---

### Post by arya885 on 2010-09-12
Hi everyone!

I am currently trying to install Hydra 5.7 on Ubuntu 10.04 I followed the following instructions (btw, I'm a total noob, so don't be afraid to write "For dummies" instructions :D): 
```
sudo apt-get install libssl-dev libgtk2.0-dev
```
```
wget -c http://freeworld.thc.org/releases/hydra-5.7-src.tar.gz
```
```
tar -xvzf hydra-5.7-src.tar.gz
```
```
cd hydra-5.7-src
```
```
make clean; ./configure
```

Then I checked if I had all the dependencies. I was missing a few ones, but I installed them all except librfc-dev because it would be a huge download to get it and I don't need it.

After this, I entered ```
make
``` and I got this error message:

[HTML]/usr/include/subversion-1/svn_diff.h:663: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_diff.h:684: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_diff.h:709: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_diff.h:738: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
In file included from hydra-svn.c:17:
/usr/include/subversion-1/svn_client.h:116: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:141: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:161: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:208: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:225: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:242: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:259: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:278: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:300: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:322: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:346: error: expected specifier-qualifier-list before ‘apr_hash_t’
/usr/include/subversion-1/svn_client.h:360: error: expected declaration specifiers or ‘...’ before ‘apr_hash_t’
/usr/include/subversion-1/svn_client.h:361: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:374: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:438: error: expected specifier-qualifier-list before ‘apr_byte_t’
/usr/include/subversion-1/svn_client.h:492: error: expected specifier-qualifier-list before ‘apr_byte_t’
/usr/include/subversion-1/svn_client.h:522: error: expected specifier-qualifier-list before ‘apr_byte_t’
/usr/include/subversion-1/svn_client.h:541: error: expected ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:551: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:561: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:572: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:597: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:597: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:624: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:624: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:651: error: expected declaration specifiers or ‘...’ before ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:653: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:685: error: expected declaration specifiers or ‘...’ before ‘apr_int64_t’
/usr/include/subversion-1/svn_client.h:694: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:709: error: expected declaration specifiers or ‘...’ before ‘apr_int64_t’
/usr/include/subversion-1/svn_client.h:714: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:779: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:795: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:848: error: expected specifier-qualifier-list before ‘apr_hash_t’
/usr/include/subversion-1/svn_client.h:922: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:972: error: expected ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:1059: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:1080: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:1098: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:1162: error: expected ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:1183: error: expected ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:1205: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:1270: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:1290: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:1347: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:1363: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:1377: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:1389: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:1432: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:1432: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:1449: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:1449: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:1462: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:1462: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:1518: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:1518: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:1534: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:1534: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:1548: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:1548: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:1616: warning: type defaults to ‘int’ in declaration of ‘apr_hash_t’
/usr/include/subversion-1/svn_client.h:1616: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:1638: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:1654: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:1717: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:1717: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:1740: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:1740: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:1757: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:1757: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:1772: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:1772: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:1829: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:1829: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:1852: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:1852: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:1878: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:1902: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:1959: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:1959: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:1981: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:1981: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2006: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:2006: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2028: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:2028: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2062: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:2062: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2119: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:2140: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:2160: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:2176: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:2256: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:2256: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2286: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:2286: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2312: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:2312: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2334: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:2334: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2362: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:2362: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2391: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:2391: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2416: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:2416: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2439: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:2439: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2475: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:2475: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2502: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:2531: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:2531: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2559: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:2640: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:2640: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2665: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:2665: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2687: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:2711: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:2711: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2734: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:2734: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2767: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:2767: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2791: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:2804: error: expected ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2831: error: expected ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2860: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:2860: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2886: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:2886: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2909: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:2938: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:2979: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:2979: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:2999: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:2999: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:3025: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:3060: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:3156: error: expected declaration specifiers or ‘...’ before ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:3161: warning: type defaults to ‘int’ in declaration of ‘apr_hash_t’
/usr/include/subversion-1/svn_client.h:3161: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:3175: error: expected declaration specifiers or ‘...’ before ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:3179: warning: type defaults to ‘int’ in declaration of ‘apr_hash_t’
/usr/include/subversion-1/svn_client.h:3179: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:3200: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:3219: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:3235: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:3324: error: expected declaration specifiers or ‘...’ before ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:3329: warning: type defaults to ‘int’ in declaration of ‘apr_hash_t’
/usr/include/subversion-1/svn_client.h:3329: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:3349: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:3367: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:3384: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:3402: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:3481: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:3481: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:3503: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:3517: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:3567: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:3584: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:3627: error: expected ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:3648: error: expected ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:3665: error: expected ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:3691: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:3734: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:3734: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:3754: error: expected ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:3770: error: expected ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:3790: error: expected ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:3867: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:3892: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:3913: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:3930: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:3952: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:3993: error: expected declaration specifiers or ‘...’ before ‘apr_uint32_t’
/usr/include/subversion-1/svn_client.h:3998: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:4015: error: expected declaration specifiers or ‘...’ before ‘apr_uint32_t’
/usr/include/subversion-1/svn_client.h:4020: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:4041: error: expected ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:4060: error: expected ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:4077: error: expected ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:4121: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:4136: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:4177: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:4177: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:4202: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:4202: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:4219: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:4236: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:4236: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:4277: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:4277: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:4313: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:4313: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:4366: error: expected specifier-qualifier-list before ‘apr_time_t’
/usr/include/subversion-1/svn_client.h:4458: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:4468: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:4520: warning: type defaults to ‘int’ in declaration of ‘apr_array_header_t’
/usr/include/subversion-1/svn_client.h:4520: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_client.h:4540: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:4568: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:4582: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:4599: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:4618: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_client.h:4637: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
In file included from hydra-svn.c:18:
/usr/include/subversion-1/svn_pools.h:49: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/subversion-1/svn_pools.h:54: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from hydra-svn.c:20:
/usr/include/subversion-1/svn_cmdline.h:65: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_cmdline.h:71: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_cmdline.h:79: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_cmdline.h:87: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_cmdline.h:97: error: expected ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_cmdline.h:111: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_cmdline.h:114: error: format string argument not a string type
/usr/include/subversion-1/svn_cmdline.h:124: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_cmdline.h:142: error: expected ‘)’ before ‘*’ token
/usr/include/subversion-1/svn_cmdline.h:154: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_cmdline.h:190: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_cmdline.h:201: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_cmdline.h:216: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_cmdline.h:231: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_cmdline.h:246: error: expected declaration specifiers or ‘...’ before ‘apr_uint32_t’
/usr/include/subversion-1/svn_cmdline.h:249: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_cmdline.h:268: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_cmdline.h:284: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_cmdline.h:297: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_cmdline.h:310: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_cmdline.h:340: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_cmdline.h:365: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
/usr/include/subversion-1/svn_cmdline.h:374: error: expected ‘)’ before ‘*’ token
hydra-svn.c:33: error: expected declaration specifiers or ‘...’ before ‘apr_pool_t’
hydra-svn.c: In function ‘my_simple_prompt_callback’:
hydra-svn.c:38: warning: implicit declaration of function ‘apr_pcalloc’
hydra-svn.c:38: error: ‘pool’ undeclared (first use in this function)
hydra-svn.c:38: error: (Each undeclared identifier is reported only once
hydra-svn.c:38: error: for each function it appears in.)
hydra-svn.c:48: warning: implicit declaration of function ‘apr_pstrdup’
hydra-svn.c: In function ‘start_svn’:
hydra-svn.c:62: error: ‘apr_pool_t’ undeclared (first use in this function)
hydra-svn.c:62: error: ‘pool’ undeclared (first use in this function)
hydra-svn.c:65: error: ‘apr_hash_t’ undeclared (first use in this function)
hydra-svn.c:65: error: ‘dirents’ undeclared (first use in this function)
hydra-svn.c:78: warning: implicit declaration of function ‘svn_pool_create_ex’
hydra-svn.c:80: error: too many arguments to function ‘svn_config_ensure’
hydra-svn.c:88: error: too many arguments to function ‘svn_client_create_context’
hydra-svn.c:94: warning: implicit declaration of function ‘svn_config_get_config’
hydra-svn.c:94: error: ‘svn_client_ctx_t’ has no member named ‘config’
hydra-svn.c:103: error: ‘apr_array_header_t’ undeclared (first use in this function)
hydra-svn.c:103: error: ‘providers’ undeclared (first use in this function)
hydra-svn.c:104: warning: implicit declaration of function ‘apr_array_make’
hydra-svn.c:106: warning: ‘svn_client_get_simple_prompt_provider’ is deprecated (declared at /usr/include/subversion-1/svn_client.h:111)
hydra-svn.c:109: error: too many arguments to function ‘svn_client_get_simple_prompt_provider’
hydra-svn.c:110: warning: implicit declaration of function ‘apr_array_push’
hydra-svn.c:113: error: too many arguments to function ‘svn_auth_open’
hydra-svn.c:120: warning: implicit declaration of function ‘svn_client_ls’
hydra-svn.c:125: warning: implicit declaration of function ‘apr_pool_clear’
hydra-svn.c:126: warning: implicit declaration of function ‘apr_pool_destroy’
hydra-svn.c:131: error: ‘svn_error_t’ has no member named ‘apr_err’
hydra-svn.c:131: error: ‘svn_error_t’ has no member named ‘message’
hydra-svn.c:134: error: ‘svn_error_t’ has no member named ‘apr_err’
hydra-svn.c:140: error: ‘svn_error_t’ has no member named ‘message’
make: *** [hydra-svn.o] Error 1
charlie@ubuntu:~/hydra-5.7-src$ 
[/HTML]

I tried to find a solution on the internet, but there doesn't seem to be something that works (I lost the entire day ](*,) )...

Can someone help me? #-o

---

### Post by david.maciejak on 2010-10-19
i know it´s quite old, but the -lpq error was for a missing postgresql lib maybe in package libpq5

---

