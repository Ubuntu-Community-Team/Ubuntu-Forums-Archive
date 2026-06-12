---
title: "Bus error (core dumped). 0%... WTF!?"
date: 2009-08-30
forum: General Help
---

### Post by ZequeZ on 2009-08-30
WARNING: Sorry for my English, it could burn your eyes if you don't take the necessaries precautions.

Well, I've installed Ubuntu on a USB memory, everything was perfect until I decided to install Amarok...

When I executed it, started to appear "crash reports", and when I tried to remove it via "apt-get remove", I got the title error...

When I try to run Amarok through console, I get:

```
amarok: error while loading shared libraries: /usr/lib/libQtNetwork.so.4: invalid ELF header

```

And when I use the command ldconfig, that I have no idea what it is, but I've read in some sites that recommend to do that, I get:

```
/sbin/ldconfig.real: /usr/lib/libQtNetwork.so.4.5.0 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libQtNetwork.so.4 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libQtNetwork.so.4.5 is not an ELF file - it has the wrong magic bytes at the start.

```

I really don't know what is happening :S
I would be very thankful if someone help me =(.

---

