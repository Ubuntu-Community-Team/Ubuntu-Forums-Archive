---
title: "Trying to compile a program sl_proxy"
date: 2009-11-30
forum: General Help
---

### Post by TheGuyWho on 2009-11-30
Hey there everyone who stumbles apon this. Ive been using ubuntu for quite a while and this is my first post heh. With that out of the way i think ill get down to business. I am trying to compile a program called SL_proxy, as you can tell this is a proxy for a game called SecondLife. 

You can get it from here if anyones interested [https://www.nsl.tuis.ac.jp/xoops/modules/xpwiki/?sl_proxy%20(E](https://www.nsl.tuis.ac.jp/xoops/modules/xpwiki/?sl_proxy%20(E))

Anyway, im pulling my hair out on why i cant seem to get this thing to compile correctly, i have all the essential libraries installed for it.. as per their very very brief documentation tells you. But i cant get it to go.. I am using ubuntu 8.10 server with basicly openssh, openssl, build-essentials, and zlib installed (after mucking around ive got zlib1-dev and some other various packages that didnt seem to help). But yeah im not too sure what todo next, if anyone has any ideas whatso ever that could help me install this i would be very greatfull :). This is what im getting after doing a sudo make to the first part of the installation.

> slproxy@TheWhoLife:~/junkbox_lib-1.1.2$ sudo make
[sudo] password for slproxy:
(cd Lib   && make)
make[1]: Entering directory `/home/slproxy/junkbox_lib-1.1.2/Lib'
(cd Doc && make )
make[2]: Entering directory `/home/slproxy/junkbox_lib-1.1.2/Lib/Doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/slproxy/junkbox_lib-1.1.2/Lib/Doc'
make[1]: Leaving directory `/home/slproxy/junkbox_lib-1.1.2/Lib'
(cd Tools && make)
make[1]: Entering directory `/home/slproxy/junkbox_lib-1.1.2/Tools'
(cd ../xLib && make)
make[2]: Entering directory `/home/slproxy/junkbox_lib-1.1.2/xLib'
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -fPIC -W -Wall -I../Lib   -DDISABLE_BERKELEYDB  -g -O2 -MT ssl_tool.o -MD -MP -MF ".deps/ssl_tool.Tpo" -c -o ssl_tool.o ssl_tool.c; \
        then mv -f ".deps/ssl_tool.Tpo" ".deps/ssl_tool.Po"; else rm -f ".deps/ssl_tool.Tpo"; exit 1; fi
In file included from ssl_tool.c:22:
ssl_tool.h:34:7: error: #error ssl_tool.h needs openSSL !!
ssl_tool.h:42:28: error: openssl/crypto.h: No such file or directory
ssl_tool.h:43:26: error: openssl/x509.h: No such file or directory
ssl_tool.h:44:25: error: openssl/pem.h: No such file or directory
ssl_tool.h:45:25: error: openssl/err.h: No such file or directory
ssl_tool.h:47:25: error: openssl/ssl.h: No such file or directory
ssl_tool.h:48:25: error: openssl/evp.h: No such file or directory
ssl_tool.h:49:26: error: openssl/rand.h: No such file or directory
In file included from ssl_tool.c:22:
ssl_tool.h:143: error: expected â)â before â*â token
ssl_tool.h:156: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
ssl_tool.h:157: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
ssl_tool.h:161: error: expected â)â before â*â token
ssl_tool.h:162: error: expected â)â before â*â token
ssl_tool.h:164: error: expected â)â before â*â token
ssl_tool.h:165: error: expected â)â before â*â token
ssl_tool.h:166: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.h:167: error: expected â)â before â*â token
ssl_tool.h:169: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.h:171: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.h:172: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.h:173: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.h:174: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.h:176: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.h:181: error: expected â)â before â*â token
ssl_tool.h:182: error: expected â)â before â*â token
ssl_tool.h:183: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.h:184: error: expected â)â before â*â token
ssl_tool.h:185: error: expected â)â before â*â token
ssl_tool.h:186: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.h:187: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.h:189: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.h:190: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.h:191: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.h:192: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.h:193: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.h:194: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.h:195: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.c:29: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
ssl_tool.c:30: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
ssl_tool.c: In function âinit_EVPAPI_Bufferâ:
ssl_tool.c:482: error: âCRYPT_Typeâ undeclared (first use in this function)
ssl_tool.c:482: error: (Each undeclared identifier is reported only once
ssl_tool.c:482: error: for each function it appears in.)
ssl_tool.c:482: warning: implicit declaration of function âEVP_aes_128_cbcâ
ssl_tool.c:486: warning: implicit declaration of function âEVP_des_ede3_cbcâ
ssl_tool.c: In function âfree_EVPAPI_Bufferâ:
ssl_tool.c:509: error: âCRYPT_Typeâ undeclared (first use in this function)
ssl_tool.c: In function âdecode_EVPAPI_Bufferâ:
ssl_tool.c:530: error: âEVP_CIPHER_CTXâ undeclared (first use in this function)
ssl_tool.c:530: error: âctxâ undeclared (first use in this function)
ssl_tool.c:534: error: âCRYPT_Typeâ undeclared (first use in this function)
ssl_tool.c:538: error: expected expression before â)â token
ssl_tool.c:539: warning: implicit declaration of function âEVP_CIPHER_CTX_initâ
ssl_tool.c:541: warning: implicit declaration of function âEVP_DecryptInit_exâ
ssl_tool.c:543: warning: implicit declaration of function âEVP_CIPHER_CTX_block_sizeâ
ssl_tool.c:546: warning: implicit declaration of function âEVP_DecryptUpdateâ
ssl_tool.c:547: warning: implicit declaration of function âEVP_DecryptFinal_exâ
ssl_tool.c:551: warning: implicit declaration of function âEVP_CIPHER_CTX_cleanupâ
ssl_tool.c: In function âencode_EVPAPI_Bufferâ:
ssl_tool.c:575: error: âEVP_CIPHER_CTXâ undeclared (first use in this function)
ssl_tool.c:575: error: âctxâ undeclared (first use in this function)
ssl_tool.c:579: error: âCRYPT_Typeâ undeclared (first use in this function)
ssl_tool.c:583: error: expected expression before â)â token
ssl_tool.c:586: warning: implicit declaration of function âEVP_EncryptInit_exâ
ssl_tool.c:593: warning: implicit declaration of function âEVP_EncryptUpdateâ
ssl_tool.c:600: warning: implicit declaration of function âEVP_EncryptFinal_exâ
ssl_tool.c: In function âsave_DHspki_with_privateâ:
ssl_tool.c:641: warning: implicit declaration of function âget_DHprivatekeyâ
ssl_tool.c:641: error: âDHkeyâ undeclared (first use in this function)
ssl_tool.c:641: error: incompatible types in assignment
ssl_tool.c: In function âread_DHspki_with_privateâ:
ssl_tool.c:667: error: âDHâ undeclared (first use in this function)
ssl_tool.c:667: error: âdhâ undeclared (first use in this function)
ssl_tool.c:678: warning: implicit declaration of function âDH_newâ
ssl_tool.c:687: warning: implicit declaration of function âBN_bin2bnâ
ssl_tool.c:695: warning: implicit declaration of function âDH_checkâ
ssl_tool.c:697: warning: implicit declaration of function âDH_freeâ
ssl_tool.c:710: error: âDHkeyâ undeclared (first use in this function)
ssl_tool.c: In function âget_DHspki_ffâ:
ssl_tool.c:749: warning: implicit declaration of function âDH_sizeâ
ssl_tool.c:749: error: âDHkeyâ undeclared (first use in this function)
ssl_tool.c: In function âgen_DHspkiâ:
ssl_tool.c:802: warning: implicit declaration of function âRAND_load_fileâ
ssl_tool.c:806: error: âDHkeyâ undeclared (first use in this function)
ssl_tool.c:806: warning: implicit declaration of function âDH_generate_parametersâ
ssl_tool.c:806: error: âDH_GENERATOR_2â undeclared (first use in this function)
ssl_tool.c:811: warning: implicit declaration of function âDH_generate_keyâ
ssl_tool.c:814: warning: implicit declaration of function âi2d_DHparamsâ
ssl_tool.c:824: warning: implicit declaration of function âBN_num_bytesâ
ssl_tool.c:833: warning: implicit declaration of function âBN_bn2binâ
ssl_tool.c: In function âgen_DHspki_fsâ:
ssl_tool.c:866: error: âDHkeyâ undeclared (first use in this function)
ssl_tool.c: In function âget_DHsharedkey_fYâ:
ssl_tool.c:967: error: âBIGNUMâ undeclared (first use in this function)
ssl_tool.c:967: error: âykâ undeclared (first use in this function)
ssl_tool.c:970: error: âDHkeyâ undeclared (first use in this function)
ssl_tool.c:973: warning: implicit declaration of function âDH_compute_keyâ
ssl_tool.c:976: warning: implicit declaration of function âBN_freeâ
ssl_tool.c: At top level:
ssl_tool.c:1193: error: expected â)â before â*â token
ssl_tool.c: In function âssl_initâ:
ssl_tool.c:1527: warning: implicit declaration of function âSSL_library_initâ
ssl_tool.c:1528: warning: implicit declaration of function âSSL_load_error_stringsâ
ssl_tool.c: At top level:
ssl_tool.c:1554: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
ssl_tool.c:1627: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â*â token
ssl_tool.c:1693: error: expected â)â before â*â token
ssl_tool.c:1719: error: expected â)â before â*â token
ssl_tool.c:1791: error: expected â)â before â*â token
ssl_tool.c:1821: error: expected â)â before â*â token
ssl_tool.c:1857: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.c: In function âssl_recv_mesgâ:
ssl_tool.c:1862: warning: implicit declaration of function âssl_recvâ
ssl_tool.c:1862: error: âsslâ undeclared (first use in this function)
ssl_tool.c: At top level:
ssl_tool.c:1909: error: expected â)â before â*â token
ssl_tool.c:1963: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.c: In function âssl_recv_mstreamâ:
ssl_tool.c:1977: error: âsslâ undeclared (first use in this function)
ssl_tool.c:1977: warning: passing argument 3 of âssl_recv_mesgâ makes integer from pointer without a cast
ssl_tool.c:1977: error: too many arguments to function âssl_recv_mesgâ
ssl_tool.c: At top level:
ssl_tool.c:2016: error: expected â)â before â*â token
ssl_tool.c:2046: error: expected â)â before â*â token
ssl_tool.c:2078: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.c: In function âssl_recv_sBufferâ:
ssl_tool.c:2083: error: âsslâ undeclared (first use in this function)
ssl_tool.c:2083: warning: passing argument 3 of âssl_recv_mesgâ makes integer from pointer without a cast
ssl_tool.c:2083: error: too many arguments to function âssl_recv_mesgâ
ssl_tool.c: At top level:
ssl_tool.c:2105: error: expected â)â before â*â token
ssl_tool.c:2129: error: expected â)â before â*â token
ssl_tool.c:2176: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.c: In function âssl_recv_mstreamBufferâ:
ssl_tool.c:2190: error: âsslâ undeclared (first use in this function)
ssl_tool.c:2190: warning: passing argument 3 of âssl_recv_sBufferâ makes integer from pointer without a cast
ssl_tool.c:2190: error: too many arguments to function âssl_recv_sBufferâ
ssl_tool.c: At top level:
ssl_tool.c:2236: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.c: In function âssl_recv_linesBufferâ:
ssl_tool.c:2244: error: âsslâ undeclared (first use in this function)
ssl_tool.c:2244: warning: passing argument 3 of âssl_recv_sBufferâ makes integer from pointer without a cast
ssl_tool.c:2244: error: too many arguments to function âssl_recv_sBufferâ
ssl_tool.c:2249: warning: passing argument 3 of âssl_recv_sBufferâ makes integer from pointer without a cast
ssl_tool.c:2249: error: too many arguments to function âssl_recv_sBufferâ
ssl_tool.c: At top level:
ssl_tool.c:2284: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.c: In function âssl_tcp_recvâ:
ssl_tool.c:2290: error: âsslâ undeclared (first use in this function)
ssl_tool.c:2290: warning: implicit declaration of function âSSL_readâ
ssl_tool.c: At top level:
ssl_tool.c:2316: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.c: In function âssl_tcp_sendâ:
ssl_tool.c:2322: error: âsslâ undeclared (first use in this function)
ssl_tool.c:2322: warning: implicit declaration of function âSSL_writeâ
ssl_tool.c: At top level:
ssl_tool.c:2355: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.c: In function âssl_tcp_recv_mesgâ:
ssl_tool.c:2360: error: âsslâ undeclared (first use in this function)
ssl_tool.c:2360: warning: passing argument 3 of âssl_tcp_recvâ makes integer from pointer without a cast
ssl_tool.c:2360: error: too many arguments to function âssl_tcp_recvâ
ssl_tool.c: At top level:
ssl_tool.c:2407: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.c: In function âssl_tcp_send_mesglnâ:
ssl_tool.c:2418: error: âsslâ undeclared (first use in this function)
ssl_tool.c:2418: warning: passing argument 3 of âssl_tcp_sendâ makes integer from pointer without a cast
ssl_tool.c:2418: error: too many arguments to function âssl_tcp_sendâ
ssl_tool.c: At top level:
ssl_tool.c:2461: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.c: In function âssl_tcp_recv_mstreamâ:
ssl_tool.c:2475: error: âsslâ undeclared (first use in this function)
ssl_tool.c:2475: warning: passing argument 3 of âssl_tcp_recv_mesgâ makes integer from pointer without a cast
ssl_tool.c:2475: error: too many arguments to function âssl_tcp_recv_mesgâ
ssl_tool.c: At top level:
ssl_tool.c:2514: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.c: In function âssl_tcp_recv_Bufferâ:
ssl_tool.c:2521: error: âsslâ undeclared (first use in this function)
ssl_tool.c: At top level:
ssl_tool.c:2546: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.c: In function âssl_tcp_send_Bufferâ:
ssl_tool.c:2552: error: âsslâ undeclared (first use in this function)
ssl_tool.c: At top level:
ssl_tool.c:2581: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.c: In function âssl_tcp_recv_sBufferâ:
ssl_tool.c:2586: error: âsslâ undeclared (first use in this function)
ssl_tool.c:2586: warning: passing argument 3 of âssl_tcp_recv_mesgâ makes integer from pointer without a cast
ssl_tool.c:2586: error: too many arguments to function âssl_tcp_recv_mesgâ
ssl_tool.c: At top level:
ssl_tool.c:2608: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.c: In function âssl_tcp_send_sBufferâ:
ssl_tool.c:2612: error: âsslâ undeclared (first use in this function)
ssl_tool.c: At top level:
ssl_tool.c:2634: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.c: In function âssl_tcp_send_sBufferlnâ:
ssl_tool.c:2642: error: âsslâ undeclared (first use in this function)
ssl_tool.c: At top level:
ssl_tool.c:2684: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.c: In function âssl_tcp_recv_mstreamBufferâ:
ssl_tool.c:2698: error: âsslâ undeclared (first use in this function)
ssl_tool.c:2698: warning: passing argument 3 of âssl_tcp_recv_sBufferâ makes integer from pointer without a cast
ssl_tool.c:2698: error: too many arguments to function âssl_tcp_recv_sBufferâ
ssl_tool.c: At top level:
ssl_tool.c:2744: error: expected declaration specifiers or â...â before âSSLâ
ssl_tool.c: In function âssl_tcp_recv_linesBufferâ:
ssl_tool.c:2752: error: âsslâ undeclared (first use in this function)
ssl_tool.c:2752: warning: passing argument 3 of âssl_tcp_recv_sBufferâ makes integer from pointer without a cast
ssl_tool.c:2752: error: too many arguments to function âssl_tcp_recv_sBufferâ
ssl_tool.c:2757: warning: passing argument 3 of âssl_tcp_recv_sBufferâ makes integer from pointer without a cast
ssl_tool.c:2757: error: too many arguments to function âssl_tcp_recv_sBufferâ
make[2]: *** [ssl_tool.o] Error 1
make[2]: Leaving directory `/home/slproxy/junkbox_lib-1.1.2/xLib'
make[1]: *** [../xLib/libextend.a] Error 2
make[1]: Leaving directory `/home/slproxy/junkbox_lib-1.1.2/Tools'
make: *** [all-tools] Error 2


---

### Post by lloyd_b on 2009-11-30
Can't speak for all the errors, but:```
ssl_tool.h:34:7: error: #error ssl_tool.h needs openSSL !!
ssl_tool.h:42:28: error: openssl/crypto.h: No such file or directory
ssl_tool.h:43:26: error: openssl/x509.h: No such file or directory
ssl_tool.h:44:25: error: openssl/pem.h: No such file or directory
ssl_tool.h:45:25: error: openssl/err.h: No such file or directory
ssl_tool.h:47:25: error: openssl/ssl.h: No such file or directory
ssl_tool.h:48:25: error: openssl/evp.h: No such file or directory
ssl_tool.h:49:26: error: openssl/rand.h: No such file or directory
``` can be fixed by installing the package "libssl-dev".  Once you've installed that, the others may or may not disappear.

Lloyd B.

---

### Post by TheGuyWho on 2009-11-30
Thanks that really pointed me in the right direction, found the rest of the libs i needed to compile it and its all good to go!
Thank you again! :)

---

