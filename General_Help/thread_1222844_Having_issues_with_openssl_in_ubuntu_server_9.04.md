---
title: "Having issues with openssl in ubuntu server 9.04"
date: 2009-07-25
forum: General Help
---

### Post by devroute on 2009-07-25
Alright so i'm trying to install psybnc but it can't find /usr/local/ssl/ and i went to cd and there's no directory so i tried apt-get install openssl and it said it was installed this is the psybnc errors when running make menuconfig any help is appreciated

```

xsubzer0x@.:~/psybnc$ make menuconfig
Initializing Menu-Configuration
[*] Running Conversion Tool for older psyBNC Data.
Using existent configuration File.
[*] Running Autoconfig.
System: Linux
Socket Libs: Internal.
Environment: Internal.
Time-Headers: in time.h and sys/time.h
Byte order: Big Endian.
IPv6-Support: Yes, general support. But no interface configured.
async-DNS-Support: Yes.
SSL-Support: Yes, but no openssl binary found in "/usr/local/ssl/".Creating Makefile
[*] Creating Menu, please wait.
This needs the ncurses library. If it is not available, menuconf wont work. If you are using curses, use make menuconfig-curses instead.
Now compile psyBNC using make, if not yet compiled, or if Options were changed.
done.
xsubzer0x@.:~/psybnc$

```

---

