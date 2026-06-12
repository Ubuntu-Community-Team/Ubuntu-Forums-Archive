---
title: "help compiling sources!!!"
date: 2009-06-29
forum: General Help
---

### Post by xmaster23 on 2009-06-29
im having problems compiling some sources like file2air and airjack heres my output when i run the make command for file2air.. any suggestions????=


cc -Wall -ggdb -g3 -pipe file2air.c -o file2air utils.o crc.o -lorcon -lm 
file2air.c:35:21: error: tx80211.h: No such file or directory
file2air.c:36:28: error: tx80211_packet.h: No such file or directory
In file included from file2air.c:43:
file2air.h:89: warning: ‘struct tx80211’ declared inside parameter list
file2air.h:89: warning: its scope is only this definition or declaration, which is probably not what you want
file2air.c: In function ‘usage’:
file2air.c:51: warning: implicit declaration of function ‘tx80211_getcardlist’
file2air.c:51: warning: assignment makes pointer from integer without a cast
file2air.c:85: error: dereferencing pointer to incomplete type
file2air.c:86: error: dereferencing pointer to incomplete type
file2air.c: At top level:
file2air.c:129: warning: ‘struct tx80211’ declared inside parameter list
file2air.c:128: error: conflicting types for ‘sendpackets’
file2air.h:88: error: previous declaration of ‘sendpackets’ was here
file2air.c: In function ‘sendpackets’:
file2air.c:133: error: storage size of ‘in_packet’ isn’t known
file2air.c:136: warning: implicit declaration of function ‘tx80211_initpacket’
file2air.c:196: warning: implicit declaration of function ‘tx80211_txpacket’
file2air.c:133: warning: unused variable ‘in_packet’
file2air.c: In function ‘main’:
file2air.c:271: error: storage size of ‘in_tx’ isn’t known
file2air.c:272: error: ‘INJ_NODRIVER’ undeclared (first use in this function)
file2air.c:272: error: (Each undeclared identifier is reported only once
file2air.c:272: error: for each function it appears in.)
file2air.c:350: warning: implicit declaration of function ‘tx80211_resolvecard’
file2air.c:385: warning: implicit declaration of function ‘tx80211_init’
file2air.c:391: warning: implicit declaration of function ‘tx80211_open’
file2air.c:399: warning: implicit declaration of function ‘tx80211_setfunctionalmode’
file2air.c:399: error: ‘TX80211_FUNCMODE_INJECT’ undeclared (first use in this function)
file2air.c:407: warning: implicit declaration of function ‘tx80211_setchannel’
file2air.c:489: warning: implicit declaration of function ‘tx80211_getcapabilities’
file2air.c:489: error: ‘TX80211_CAP_SEQ’ undeclared (first use in this function)
file2air.c:512: error: ‘TX80211_CAP_FRAG’ undeclared (first use in this function)
file2air.c:563: warning: implicit declaration of function ‘tx80211_close’
file2air.c:271: warning: unused variable ‘in_tx’
make: *** [file2air] Error 1
root@buNKEr:/home/bunker/Desktop/file2air# make install
make: *** No rule to make target `install'.  Stop.
root@buNKEr:/home/bunker/Desktop/file2air# make
cc -Wall -ggdb -g3 -pipe file2air.c -o file2air utils.o crc.o -lorcon -lm 
file2air.c:35:21: error: tx80211.h: No such file or directory
file2air.c:36:28: error: tx80211_packet.h: No such file or directory
In file included from file2air.c:43:
file2air.h:89: warning: ‘struct tx80211’ declared inside parameter list
file2air.h:89: warning: its scope is only this definition or declaration, which is probably not what you want
file2air.c: In function ‘usage’:
file2air.c:51: warning: implicit declaration of function ‘tx80211_getcardlist’
file2air.c:51: warning: assignment makes pointer from integer without a cast
file2air.c:85: error: dereferencing pointer to incomplete type
file2air.c:86: error: dereferencing pointer to incomplete type
file2air.c: At top level:
file2air.c:129: warning: ‘struct tx80211’ declared inside parameter list
file2air.c:128: error: conflicting types for ‘sendpackets’
file2air.h:88: error: previous declaration of ‘sendpackets’ was here
file2air.c: In function ‘sendpackets’:
file2air.c:133: error: storage size of ‘in_packet’ isn’t known
file2air.c:136: warning: implicit declaration of function ‘tx80211_initpacket’
file2air.c:196: warning: implicit declaration of function ‘tx80211_txpacket’
file2air.c:133: warning: unused variable ‘in_packet’
file2air.c: In function ‘main’:
file2air.c:271: error: storage size of ‘in_tx’ isn’t known
file2air.c:272: error: ‘INJ_NODRIVER’ undeclared (first use in this function)
file2air.c:272: error: (Each undeclared identifier is reported only once
file2air.c:272: error: for each function it appears in.)
file2air.c:350: warning: implicit declaration of function ‘tx80211_resolvecard’
file2air.c:385: warning: implicit declaration of function ‘tx80211_init’
file2air.c:391: warning: implicit declaration of function ‘tx80211_open’
file2air.c:399: warning: implicit declaration of function ‘tx80211_setfunctionalmode’
file2air.c:399: error: ‘TX80211_FUNCMODE_INJECT’ undeclared (first use in this function)
file2air.c:407: warning: implicit declaration of function ‘tx80211_setchannel’
file2air.c:489: warning: implicit declaration of function ‘tx80211_getcapabilities’
file2air.c:489: error: ‘TX80211_CAP_SEQ’ undeclared (first use in this function)
file2air.c:512: error: ‘TX80211_CAP_FRAG’ undeclared (first use in this function)
file2air.c:563: warning: implicit declaration of function ‘tx80211_close’
file2air.c:271: warning: unused variable ‘in_tx’
make: *** [file2air] Error 1

---

### Post by t4thfavor on 2009-06-29
did you .configure? Not sure, but it sounds like something didn't get generated when you started the compile, and thats why there are lots of missing vars.


Nevermind there is no ./configure. It appears you ned LORCON, but the site in the link is down... go figure.

---

