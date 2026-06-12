---
title: "Installing SIPp on Ubuntu 11.04"
date: 2011-10-06
forum: General Help
---

### Post by etienned on 2011-10-06
Good day,

I am currently trying to install SIPp on my PC by using the following commands

$ sudo apt-get install ncurses-dev
$ sudo apt-get install build-essential
#Grab sipp 3.1 from sourceforge.net 
$ wget -m -nd [http://downloads.sourceforge.net/project/sipp/sipp/3.1/sipp.3.1.src.tar.gz](http://downloads.sourceforge.net/project/sipp/sipp/3.1/sipp.3.1.src.tar.gz)
#extract it locally
$ tar -xzf sipp.3.1.src.tar.gz
$ cd sipp.svn [FONT=Verdana]
[/FONT]Open ./sipp.svn/scenario.hpp and add this line[FONT=Verdana]
[/FONT]
#include <limits.h>[FONT=Verdana]
[/FONT]after[FONT=Verdana]
[/FONT]#include <sys/socket.h>[FONT=Verdana]
[/FONT]save the file, and in the terminal do [FONT=monospace][/FONT][FONT=Verdana]
[/FONT]$make pcapplay

But when I execute the make pcapplay command the following error exists.

[email]etienne@ubuntu:~/Public/sipp.svn[/email]$ make pcapplay
make OSNAME=`uname|sed -e "s/CYGWIN.*/CYGWIN/"` MODELNAME=`uname -m|sed "s/Power Macintosh/ppc/"` OBJ_PCAPPLAY="send_packets.o prepare_pcap.o" PCAPPLAY_LIBS="-lpcap" PCAPPLAY="-DPCAPPLAY" sipp
make[1]: Entering directory `/home/etienne/Public/sipp.svn'
gcc   -D__LINUX -pthread  -DSVN_VERSION="\"unknown\""  -DPCAPPLAY     -I. -I/usr/include/openssl  -c -o send_packets.o send_packets.c
send_packets.c:44:18: fatal error: pcap.h: No such file or directory
compilation terminated.
make[1]: *** [send_packets.o] Error 1
make[1]: Leaving directory `/home/etienne/Public/sipp.svn'
make: *** [pcapplay] Error 2

Can someone please assist or provide me with a method of installing SIPp

---

### Post by y2pk001 on 2011-10-06
Try installing pcaputils 

sudo apt-get install pcaputils

Cheers

---

### Post by etienned on 2011-10-06
Thanks

It still gives the same error

---

### Post by sweni on 2011-10-10
I had the same problem.

After apt-get install libssl-dev libpcap-dev libncurses5-dev

the problem was resolved.

I think the libpcap-dev was what I needed.

---

### Post by etienned on 2011-10-11
Thank you for your help, it worked

---

