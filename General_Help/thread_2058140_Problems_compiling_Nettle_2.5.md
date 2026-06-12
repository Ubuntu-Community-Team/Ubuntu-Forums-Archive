---
title: "Problems compiling Nettle 2.5"
date: 2012-09-15
forum: General Help
---

### Post by jonathanrainer on 2012-09-15
Hi, I'm a bit of beginner to Ubuntu but I've used it a fair bit now and am becoming more proficient but the problem I've reached has stumped me and so I hope that someone here can help me to solve it.

Anyway, I'm trying to compile FileZilla 3.5.2 for my Ubuntu Server so that I can interface with a SeedBox that I rent. The reason for this is the Seedbox won't connect to FileZilla 3.5.3 due to fatal TLS errors when it does but I know that it works with 3.5.2 as that's the version I use on my Mac to connect to it. So I downloaded the older release and followed the INSTALL instructions to compile it but there were some prerequisites missing, paticularly gnuTLS which itself requires Nettle 2.5 and 2.4 is the standard included in Ubuntu.

So I promptly downloaded Nettle 2.5 and ran the configure script and this executed fine but then when I run the make command is where I run into problems. The terminal spits back this error:

```
make all-here
make[1]: Entering directory `/home/jonathanrainer/Documents/nettle-2.5'
m4 ./asm.m4 machine.m4 config.m4 \
        aes-decrypt-internal.asm >aes-decrypt-internal.s
/bin/sh: 1: m4: not found
make[1]: *** [aes-decrypt-internal.o] Error 127
make[1]: Leaving directory `/home/jonathanrainer/Documents/nettle-2.5'
make: *** [all] Error 2

```

And I'll be honest and say I've tried to decode it but I can't make sense of what it's saying, can anyone help? 

I'm running Ubuntu Server 12.04.1 - 32Bit, thank you very much in advance.

(In addition if anyone has an easier way of installing some of these packages than having to compile from source I'm all ears but I couldn't find the packages I need using apt-get as their not as recent as is necessary but if I'm wrong I'm more than willing to admit that since I am somewhat new to this game.)

---

