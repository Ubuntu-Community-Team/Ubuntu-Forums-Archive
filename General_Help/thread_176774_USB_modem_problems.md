---
title: "USB modem problems"
date: 2006-05-15
forum: General Help
---

### Post by nikolaos on 2006-05-15
Hi everyone, this is my first thread (i hope i am in the correct forum). I am a linux-Ubuntu newbie and my problem is that i have a BT broadband with 
USB Modem:Voyager 105. 
I downloaded the driver from [http://eciadsl.flashtux.org](http://eciadsl.flashtux.org)
and installed it with 
dpkg -i /path/eciadsl-usermode_0.11-1_i386.deb 
I was asked to installed pppoe which i did, so everything is perfect so far.
i configured with eciadsl-config-text BUT when i try to run the driver i get this:
```
nick@Bangs:~$ sudo eciadsl-start

[EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is OK

[EciAdsl 2/5] Uploading firmware...

Process skipped .. no more needed
firmware loaded successfully

[EciAdsl 3/5] Synchronization...

OK eciadsl-synch: success 
Synchronization successful

[EciAdsl 4/5] Connecting to provider...

using channel 2
Using interface ppp0
Connect: ppp0 <--> /dev/pts/2
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 31324), status = 0x0
Modem hangup
Connection terminated.
```

then i CTRL-C and i get

```
Terminating on signal 2
ERROR: failed to connect
nick@Bangs:~$
```

can anyone help?

---

