---
title: "install / run j2eesdk-1_4_03-linux.bin"
date: 2011-07-12
forum: General Help
---

### Post by Mappenz on 2011-07-12
Hi,

i should install a old version of Java EE, so i can write code for a old kind of webservice.

Here's what happens:
```
michael@michi:~/Downloads$ ./j2eesdk-1_4_03-linux.bin 
./j2eesdk-1_4_03-linux.bin: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

```

I looked for the library in Synaptic, but there are only newer versions of libstdc++. I couldn't find a solution to this problem i was able to follow. So i would be very happy if someone could come up with a simple solution.

Michi

---

### Post by Gyokuro on 2011-07-12
You will not find this in a current Ubuntu system and it think it must be a Gutsy release. The file you will need is

libstdc++2.10-glibc2.2 

or you search for a debian package like libstdc++2.10-glibc2.2_2.95.4-24_i386.deb. In case it's possible install such an old sytem in a KVM machine. Providing service for an old system is always an adventure.

HTH

---

### Post by Mappenz on 2011-07-12
Thanks, 

thats a good anwer. Since i have no experience in virtualisation i am tempted to just install it. Could that break the newer jdk or anything else in my system?

---

### Post by Gyokuro on 2011-07-13
Not in a virtualized environment but it's always good to try such things in KVM/Virtualbox and later put it on the real metal - however always have backups!

---

