---
title: "Which should I use?"
date: 2010-10-26
forum: General Help
---

### Post by LinuxIsAmazing on 2010-10-26
Which version of Ubuntu should I use? 64-bit or 32-bit? I hear different answers all the time. I have an HP with an AMD Anthlon 64-bit dual core. If it is not as simple as a use this or that, what are the pros and cons of each? I appreciate all the help. Thank you very much. :)

---

### Post by tgm4883 on 2010-10-26
> **LinuxIsAmazing said:**
> Which version of Ubuntu should I use? 64-bit or 32-bit? I hear different answers all the time. I have an HP with an AMD Anthlon 64-bit dual core. If it is not as simple as a use this or that, what are the pros and cons of each? I appreciate all the help. Thank you very much. :)

Nope, it's that simple. Use 64-bit

---

### Post by CharlesA on 2010-10-26
There's a rather lengthy discussing in recurring discussions about the whole 32-bit vs 64-bit thing, but I'll leave this thread here for the time being.

---

### Post by lyall on 2010-10-26
for your machine - 64-bit
it will use the CPU the best
the 32-bit is basically for single core CPU

to answer you own question download both the 32-bit and 64-bit and test them by using System Monitor and see how the CPU is used.
to get a good test you should use the same apps

good luck and have fun learning

---

### Post by yetiman64 on 2010-10-26
> **LinuxIsAmazing said:**
> Which version of Ubuntu should I use? 64-bit or 32-bit? I hear different answers all the time. I have an HP with an AMD Anthlon 64-bit dual core. If it is not as simple as a use this or that, what are the pros and cons of each? I appreciate all the help. Thank you very much. :)

If you have 4 GB or more of RAM, I would suggest the use of 64 bit to get the most of your hardware as 32 bit will generally address only about 3.2 GB of RAM (without the installation of a pae --physical address extension-- kernel, note this type of kernel is installed by default since Karmic on >4GB RAM hardware so the point is probably no longer of too much concern).

My personal perception is it seems to run slightly faster than the 32 bit installs on the same hardware (6 parallel installs of Ubuntu here on the same HDD, Jaunty Lucid and Maverick each in both 32 and 64 bit variants --I'm a bit of a sucker for dual boot punishment :)).

32 bit generally seems better supported particularly with regard to flash support and non native (read Windows) codecs. However Adobe has recently made available a preview version for 64 bit, codenamed "square". I use it here and have next to no trouble with it despite the fact it is not openly released (it is "pre-release software"). You can read about it, or download it from [--here--]("http://labs.adobe.com/technologies/flashplayer10/"). (Note, it is not automatically updated and its installation is manual).

I personally think the differences are minor. Hope you enjoy whichever you choose.

---

### Post by 3rdalbum on 2010-10-26
> **lyall said:**
> the 32-bit is basically for single core CPU

No. 64-bit does not mean "two 32-bit cores equals 64-bit". It's about the length of numbers represented in the CPU. There are dual-core 32-bit CPUs, and you can use multiple cores in a 32-bit operating system.

To answer the OP: If you have a 64-bit CPU and more than 1 GiB of RAM, use 64-bit. Otherwise, use 32-bit.

---

