---
title: "Alternative command for snoop"
date: 2010-01-27
forum: General Help
---

### Post by wizard_1979 on 2010-01-27
Hi all,

i'm used to input the following command when tracing a port or interface in Solaris 9/10. This a packet sniffer.

==================================

snoop -o <Outputfile.txt> -x -ip <TraceIP>

==================================

is there a packet sniffer command which performs this on Ubuntu 9.04 (Jaunty)?

Thanks and regards,

Matthew

---

### Post by rnerwein on 2010-01-27
hi
you can use: tcpdump
ciao

sorry i forgot see: [http://packages.ubuntu.com/jaunty/tcpdump](http://packages.ubuntu.com/jaunty/tcpdump)

---

