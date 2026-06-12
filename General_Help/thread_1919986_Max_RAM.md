---
title: "Max RAM"
date: 2012-02-03
forum: General Help
---

### Post by dRounse on 2012-02-03
I was reading someones comment on youtube and they said that 32-bit OS can only support 3Gb of RAM but why would the Motherboard allow more? Also they said that there is an 8Gb limit per RAM slot... It just doesnt make sense to me, any clarifications?

---

### Post by jerrrys on 2012-02-03
The standard 32 bit Linux kernel supports 4g of ram.  The modified 32 bit kernel (known as the server or PAE kernel) can support 32G of ram.

---

### Post by dRounse on 2012-02-03
> **jerrrys said:**
> The standard 32 bit kernel supports 4g of ram.  The modified 32 bit kernel (known as the server or PAE kernel) can support 32G of ram.

Is that just Linux or Windows XP and on?

---

### Post by mr clark25 on 2012-02-03
answering a couple other questions:

as jerrys said, the regular 32-bit kernel will only support so much ram. the pae kernel will support far more, and the 64bit kernel does aswell.

i believe ubuntu will install the pae kernel automatically if you have >3gb of ram.


the 8gb per ram slot is a limitation on either the motherboard or the memory controller, which can be either on the motherboard or the cpu, depending on the cpu type.

---

### Post by dRounse on 2012-02-03
> **mr clark25 said:**
> answering a couple other questions:

as jerrys said, the regular 32-bit kernel will only support so much ram. the pae kernel will support far more, and the 64bit kernel does aswell.

i believe ubuntu will install the pae kernel automatically if you have >3gb of ram.


the 8gb per ram slot is a limitation on either the motherboard or the memory controller, which can be either on the motherboard or the cpu, depending on the cpu type.

Ok thanks for the clarification

---

### Post by 3rdalbum on 2012-02-04
A 32 bit operating system can only use 4 GiB of RAM (usually less, for a reason). This applies to Windows too - with only 32 bits in the memory address you simply don't have enough digits to refer to any more memory.

The PAE kernels on Linux and Windows Server can address more - but only because they actually use 36-bit memory addresses, and only on CPUs that understand 36-bit addresses.

---

### Post by jerrrys on 2012-02-04
@3rdalbum:

10000+;  you planning on leaving any beans for the rest of us?

---

