---
title: "Streams PCAP compile errors"
date: 2011-11-29
forum: General Help
---

### Post by DaveVato on 2011-11-29
Trying to install Streams0.1.0 in ubuntu 11.10 64 bit
[http://www.honeynet.org/node/633](http://www.honeynet.org/node/633)



Getting an error I cant get rid of during the compile.

I have installed the libreadline 6  with dev and ruby packages.

```

.
.
.
checking whether make sets $(MAKE)... (cached) yes
checking for size_t... yes
checking whether debug code generation should be enabled... no
checking pcap.h usability... yes
checking pcap.h presence... yes
checking for pcap.h... yes
checking for pcap_datalink in -lpcap... yes
checking readline.h usability... no
checking readline.h presence... no
checking for readline.h... no
   Error - libreadline headers not found.


```

---

### Post by kiulu on 2012-07-11
Assuming readline.h exists in /usr/include/readline, the following command worked for me:

```
./configure --with-libreadline-includes=/usr/include/readline
```I found this option by scanning through configure.ac

---

