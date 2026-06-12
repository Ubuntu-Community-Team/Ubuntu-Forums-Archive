---
title: "can i install this program? i think i need some help."
date: 2006-02-06
forum: General Help
---

### Post by ice60 on 2006-02-06
hi, i want to install a small program called tcpdstat. i think i have found the home page but there's not much help for installing it. it's really small, can someone have alook at it and tell me if i can install it? thanks.
[http://staff.washington.edu/dittrich/talks/core02/tools/tools.html](http://staff.washington.edu/dittrich/talks/core02/tools/tools.html)

---

### Post by nanotube on 2006-02-06
that tcpdstat package is a .tar file - tar is a type of archive. and inside that archive is C source. so first, you have to untar the package (use gui, or from commandline, "tar -xvf tcpdstat-uw.tar".

once you have it untarred, you will have to compile it... probably have to install the "build-essential" package from synaptic first, in the terminal cd to that directory, and type "make". that will compile everything. then if you type "make install" it should install (but have to do it as root, probably. as in, "sudo make install")

---

### Post by ice60 on 2006-02-07
thanks for the help. i tried it but i get lots of errors. that's really why i posted - i don't know how to tell if it's safe to install something. how can i install this program? thanks.

i have got build-essential. maybe it's not for linux though. i'm sure there's a linux version. can i ask for it to be put into synaptic?

```
$ make
cc  -I. -I../libpcap-0.7.1 -DLINUX -D__FAVOR_BSD -D_LARGEFILE_SOURCE=1 -D_FILE_OFFSET_BITS=64 -L../libpcap-0.7.1 -c stat.c
cc  -I. -I../libpcap-0.7.1 -DLINUX -D__FAVOR_BSD -D_LARGEFILE_SOURCE=1 -D_FILE_OFFSET_BITS=64 -L../libpcap-0.7.1 -c net_read.c
net_read.c:86:18: error: pcap.h: No such file or directory
net_read.c:117: warning: &#8216;struct pcap_pkthdr&#8217; declared inside parameter list
net_read.c:117: warning: its scope is only this definition or declaration, which is probably not what you want
net_read.c:119: warning: &#8216;struct pcap_pkthdr&#8217; declared inside parameter list
net_read.c:121: warning: &#8216;struct pcap_pkthdr&#8217; declared inside parameter list
net_read.c:123: warning: &#8216;struct pcap_pkthdr&#8217; declared inside parameter list
net_read.c:125: warning: &#8216;struct pcap_pkthdr&#8217; declared inside parameter list
net_read.c:127: warning: &#8216;struct pcap_pkthdr&#8217; declared inside parameter list
net_read.c:143: error: &#8216;PCAP_ERRBUF_SIZE&#8217; undeclared here (not in a function)
net_read.c:146: error: syntax error before &#8216;*&#8217; token
net_read.c:146: warning: data definition has no type or storage class
net_read.c:149: error: static declaration of &#8216;packet_length&#8217; follows non-static declaration
tcpdstat.h:415: error: previous declaration of &#8216;packet_length&#8217; was here
net_read.c:157: warning: &#8216;struct pcap_pkthdr&#8217; declared inside parameter list
net_read.c:171: error: syntax error before &#8216;pcap_handler&#8217;
net_read.c:171: warning: no semicolon at end of struct or union
net_read.c:173: error: syntax error before &#8216;}&#8217; token
net_read.c:175: error: array type has incomplete element type
net_read.c:176: error: &#8216;DLT_EN10MB&#8217; undeclared here (not in a function)
net_read.c:177: error: &#8216;DLT_FDDI&#8217; undeclared here (not in a function)
net_read.c:181: error: &#8216;DLT_PPP&#8217; undeclared here (not in a function)
net_read.c:182: error: &#8216;DLT_NULL&#8217; undeclared here (not in a function)
net_read.c:187: error: syntax error before &#8216;lookup_printer&#8217;
net_read.c: In function &#8216;lookup_printer&#8217;:
net_read.c:191: error: dereferencing pointer to incomplete type
net_read.c:191: error: increment of pointer to unknown structure
net_read.c:191: error: arithmetic on pointer to an incomplete type
net_read.c:192: error: dereferencing pointer to incomplete type
net_read.c:193: error: dereferencing pointer to incomplete type
net_read.c:197: warning: return makes integer from pointer without a cast
net_read.c: In function &#8216;open_dump&#8217;:
net_read.c:209: warning: assignment makes pointer from integer without a cast
net_read.c:213: warning: assignment makes pointer from integer without a cast
net_read.c:215: warning: passing argument 1 of &#8216;fileno&#8217; makes pointer from integer without a cast
net_read.c: At top level:
net_read.c:235: warning: &#8216;struct pcap_pkthdr&#8217; declared inside parameter list
net_read.c:236: error: conflicting types for &#8216;dump_reader&#8217;
net_read.c:117: error: previous declaration of &#8216;dump_reader&#8217; was here
net_read.c: In function &#8216;dump_reader&#8217;:
net_read.c:243: error: dereferencing pointer to incomplete type
net_read.c:244: error: dereferencing pointer to incomplete type
net_read.c:246: error: dereferencing pointer to incomplete type
net_read.c:248: error: dereferencing pointer to incomplete type
net_read.c:249: error: dereferencing pointer to incomplete type
net_read.c:250: error: dereferencing pointer to incomplete type
net_read.c:252: error: dereferencing pointer to incomplete type
net_read.c:259: error: dereferencing pointer to incomplete type
net_read.c:260: error: dereferencing pointer to incomplete type
net_read.c:265: error: dereferencing pointer to incomplete type
net_read.c:266: error: dereferencing pointer to incomplete type
net_read.c:277: error: dereferencing pointer to incomplete type
net_read.c:282: warning: passing argument 2 of &#8216;net_reader&#8217; from incompatible pointer type
net_read.c: At top level:
net_read.c:287: warning: &#8216;struct pcap_pkthdr&#8217; declared inside parameter list
net_read.c:288: error: conflicting types for &#8216;ether_if_read&#8217;
net_read.c:119: error: previous declaration of &#8216;ether_if_read&#8217; was here
net_read.c: In function &#8216;ether_if_read&#8217;:
net_read.c:289: error: dereferencing pointer to incomplete type
net_read.c:290: error: dereferencing pointer to incomplete type
net_read.c: At top level:
net_read.c:337: warning: &#8216;struct pcap_pkthdr&#8217; declared inside parameter list
net_read.c:338: error: conflicting types for &#8216;fddi_if_read&#8217;
net_read.c:121: error: previous declaration of &#8216;fddi_if_read&#8217; was here
net_read.c: In function &#8216;fddi_if_read&#8217;:
net_read.c:339: error: dereferencing pointer to incomplete type
net_read.c:340: error: dereferencing pointer to incomplete type
net_read.c: At top level:
net_read.c:420: warning: &#8216;struct pcap_pkthdr&#8217; declared inside parameter list
net_read.c:421: error: conflicting types for &#8216;atm_if_read&#8217;
net_read.c:123: error: previous declaration of &#8216;atm_if_read&#8217; was here
net_read.c: In function &#8216;atm_if_read&#8217;:
net_read.c:422: error: dereferencing pointer to incomplete type
net_read.c:423: error: dereferencing pointer to incomplete type
net_read.c: At top level:
net_read.c:457: warning: &#8216;struct pcap_pkthdr&#8217; declared inside parameter list
net_read.c:458: error: conflicting types for &#8216;ppp_if_read&#8217;
net_read.c:125: error: previous declaration of &#8216;ppp_if_read&#8217; was here
net_read.c: In function &#8216;ppp_if_read&#8217;:
net_read.c:459: error: dereferencing pointer to incomplete type
net_read.c:460: error: dereferencing pointer to incomplete type
net_read.c: At top level:
net_read.c:472: warning: &#8216;struct pcap_pkthdr&#8217; declared inside parameter list
net_read.c:473: error: conflicting types for &#8216;null_if_read&#8217;
net_read.c:127: error: previous declaration of &#8216;null_if_read&#8217; was here
net_read.c: In function &#8216;null_if_read&#8217;:
net_read.c:474: error: dereferencing pointer to incomplete type
net_read.c:475: error: dereferencing pointer to incomplete type
make: *** [net_read.o] Error 1

```

---

### Post by nanotube on 2006-02-08
hi
build-essential IS in synaptic already. just search for it in synaptic.

from your error log, looks like the program demands libpcap source to compile. so you have to go and install package libpcap0.7-dev or libpcap0.8-dev. and then it could work. :)
but really... why not just find another packet analyzer program that /is/ in synaptic? for example, "ethereal" is an excellent packet monitor/analyzer, with a nice gui, too. just search for it in synaptic (make sure you have added the universe repository first).

---

### Post by ice60 on 2006-02-08
[QUOTE=nanotube]hi
build-essential IS in synaptic already. just search for it in synaptic.

from your error log, looks like the program demands libpcap source to compile. so you have to go and install package libpcap0.7-dev or libpcap0.8-dev. and then it could work. :)
but really... why not just find another packet analyzer program that /is/ in synaptic? for example, "ethereal" is an excellent packet monitor/analyzer, with a nice gui, too. just search for it in synaptic (make sure you have added the universe repository first).[/QUOTE]
thanks, nanotube . i'll try one of the libpcaps. 

i would probably have recommended ethereal too, but i'm following an article about traffic analysis which uses some very good tools other then ethereal. here's something from the article

>  you may share the sentiments of a student in one of the author&#8217;s recent classes who said &#8220;I&#8217;m embarrassed I ever used Ethereal to start network analysis!&#8221;

so that's why i'm trying to install tcpdstat. it's not one of the most important tools though and some of the other tools where in synaptic.

---

