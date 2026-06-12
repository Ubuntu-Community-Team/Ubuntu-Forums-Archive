---
title: "OpenSSL handshake failure"
date: 2010-11-10
forum: General Help
---

### Post by beowulf222 on 2010-11-10
Hi,

I am using fetchmail (with ssl support) to download my e-mail. About a week ago, the downloading from two servers stopped, among them gmail.com, due to an ssl error. Usually that means updating the ssl fingerprint in fetchmail.conf, and when I wanted to do this I discovered that there seems to a issue with openssl.

When I do openssl s_client -connect pop.gmail.com:995 -showcerts I now get an error

server:> openssl s_client -connect pop.gmail.com:995 -showcerts 

CONNECTED(00000003)
5448:error:140790E5:SSL routines:SSL23_WRITE:ssl handshake failure:s23_lib.c:188:

Ubuntu 8.04 (2.6.24-28-server #1 SMP Sat Oct 16 17:53:34 UTC 2010 i686 GNU/Linux)
OpenSSL 0.9.8g 19 Oct 2007

Can anybody explain to me what the error means and how to fix it?

-- nick

---

### Post by beowulf222 on 2010-11-11
Hi,

Nobody has any idea or nobody used openssl?

If I do a debug of the command, I get the following.

server:>openssl s_client -connect pop.gmail.com:995 -showcerts -debug

CONNECTED(00000003)
write to 0x80c4988 [0x80c49d0] (121 bytes => 121 (0x79))
0000 - 80 77 01 03 01 00 4e 00-00 00 20 00 00 39 00 00   .w....N... ..9..
0010 - 38 00 00 35 00 00 16 00-00 13 00 00 0a 07 00 c0   8..5............
0020 - 00 00 33 00 00 32 00 00-2f 03 00 80 00 00 05 00   ..3..2../.......
0030 - 00 04 01 00 80 00 00 15-00 00 12 00 00 09 06 00   ................
0040 - 40 00 00 14 00 00 11 00-00 08 00 00 06 04 00 80   @...............
0050 - 00 00 03 02 00 80 00 00-ff 49 46 ba 5f c1 c5 50   .........IF._..P
0060 - 87 47 f7 8f 7b 57 a9 43-81 5b 26 2f 73 29 92 95   .G..{W.C.[&/s)..
0070 - e3 90 44 a7 16 83 62 e2-24                        ..D...b.$
read from 0x80c4988 [0x80c9f30] (7 bytes => 0 (0x0))
5448:error:140790E5:SSL routines:SSL23_WRITE:ssl handshake failure:s23_lib.c:188:

Alternative, how if I compile a newer version of openssl myself, how can I make Ubuntu use that newer installation instead of the old one from the package?

---

