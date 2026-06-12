---
title: "A Question About Ubuntu/Jaunty..."
date: 2009-07-05
forum: General Help
---

### Post by b@sh_n3rd on 2009-07-05
Hey I'm planning to build a new PC, (which I call "TiTANIUM"). The mobo I chose supports up to 16GiB of RAM. Now I wouldn't need that kinda mem. In fact, max would be about 4 that I'd use at the beginning, but while browsing through various brands I noted that Windows recognizes only a certain amount of mem maximum. So I was just wondering, how much of RAM does Jaunty support? *Jaunty*, coz that's the latest distro and that's what I'm using right now...Thanks in advance...

---

### Post by ibutho on 2009-07-05
The 64 bit version should support your 16GB of RAM, but the 32 bit version supports about 4GB of RAM. Some distros tinker with their 32 bit kernels so that they support more than 4GB, but I am not sure if this is enabled in the generic 32 bit Ubuntu kernel.

---

### Post by monsterstack on 2009-07-05
> **b@sh_n3rd said:**
> Hey I'm planning to build a new PC, (which I call "TiTANIUM"). The mobo I chose supports up to 16GiB of RAM. Now I wouldn't need that kinda mem. In fact, max would be about 4 that I'd use at the beginning, but while browsing through various brands I noted that Windows recognizes only a certain amount of mem maximum. So I was just wondering, how much of RAM does Jaunty support? *Jaunty*, coz that's the latest distro and that's what I'm using right now...Thanks in advance...

Jaunty 32-bit will support up to 4gigabytes, unless you install a PAE-aware kernel ( which is just a case of running *sudo sudo apt-get install linux-headers-server linux-image-server linux-server* ). Some people reckon PAE is not as useful as it first appears, though. 64-bit Linux has so much address space for memory that you'll be hard-pressed to reach it in your lifetime. 64 gigabytes? No problem. I've no idea what you'd use it for. Some servers that do a lot of work run entirely on RAM. Google pretty much runs on the stuff, for instance. Perhaps you could include a battery in your machine, and create an entirely RAM-based version of Jaunty. When she boots, the entire contents of the hard-disk is loaded into RAM-disk partitions. Now that would be lightning fast. When you shut down or get a power out, everything gets transferred back to disk. Smooth.

Edit: reading comprehension fail. I read 16 as 64. Doh.

---

### Post by b@sh_n3rd on 2009-07-05
> **monsterstack said:**
> Jaunty 32-bit will support up to 4gigabytes, unless you install a PAE-aware kernel ( which is just a case of running *sudo sudo apt-get install linux-headers-server linux-image-server linux-server* ). Some people reckon PAE is not as useful as it first appears, though. 64-bit Linux has so much address space for memory that you'll be hard-pressed to reach it in your lifetime. 64 gigabytes? No problem. I've no idea what you'd use it for. Some servers that do a lot of work run entirely on RAM. Google pretty much runs on the stuff, for instance. Perhaps you could include a battery in your machine, and create an entirely RAM-based version of Jaunty. When she boots, the entire contents of the hard-disk is loaded into RAM-disk partitions. Now that would be lightning fast. When you shut down or get a power out, everything gets transferred back to disk. Smooth.

Edit: reading comprehension fail. I read 16 as 64. Doh.

Hi guys, thanks for replying. **monsterstack** your idea *is* pretty cool but I *did* mention that I wouldn't need that much of memory :D...It's just the mobo I chose and I didn't do that coz of the capacity...I mean I discovered *that* long after I'd chosen the mobo and it made me hit the ceiling...anyways, I asked this Q coz I was just wondering if Ubuntu'd make full use of my PC...winblows wouldn't...

Oh yeah, btw, I *am* planning to use the 64bit version, so that's ok...I'm gonna use an AMD Phenom II 955...(which is why I chose this mobo :D)

---

### Post by joeinbend on 2009-09-22
Hi B@sh, I'm wondering how your build came out? I'm planning on doing an upgrade to my primary server as well, and want to use a Phenom II 955 overclocked, with 8GB RAM, and run 9.04 Server 64-bit. I want to make sure that it will be able to utilize all 4 cores of that CPU. I'd be a shame to buy such a fast chip and find out it's not able to utilize it!!!

---

### Post by doas777 on 2009-09-22
yep, as others have said, it's all about the 32bit/64bit choice. in 32 bit the biggest number you can express is 2^32 - 1 => 4294967295, which means that a 32 bit system can only provide that many memory addresses. it comes out to about 3.8GB after you convert from GiB to GB. 64bit systems have a doubled memory space, so you can have up to 18446744073709551615 addresses giving you much more room. most vendors limit the 64bit mem address to 48 or 52 bits, but it is still a heck of an improvement.

---

