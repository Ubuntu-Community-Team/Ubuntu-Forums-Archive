---
title: "Realtim kernel"
date: 2010-07-16
forum: General Help
---

### Post by hungtdhbk on 2010-07-16
Hello everyone!
I am using Ubuntu 10.04 to develope embedded systems. I've studied about Ubuntu so I want to ask you a question. If you know, please help me.
- Is Ubuntu kernel  Linux kernel? Are there differences between other distributions of Linux/GNU(red Hat,debian...)?
- Ubuntu kernel is realtime kernel? 
- In embedded systems required RTOS, is Ubuntu used?

---

### Post by Vectorferret on 2010-07-16
> **hungtdhbk said:**
> Hello everyone!
I am using Ubuntu 10.04 to develope embedded systems. I've studied about Ubuntu so I want to ask you a question. If you know, please help me.
- Is Ubuntu kernel  Linux kernel? 
Yes.
> **hungtdhbk said:**
> Are there differences between other distributions of Linux/GNU(red Hat,debian...)?
Yes. Different distributions can have different versions of the kernel, different installers and almost always have differences in what they install that isn't the kernel.
> **hungtdhbk said:**
> - Ubuntu kernel is realtime kernel? Depends on how real time you need. Linux can not really be considered a hard real time system, but in most cases will do soft real time better than Windows Embedded.
> **hungtdhbk said:**
> - In embedded systems required RTOS, is Ubuntu used?I don't know. Probably not. An embedded system needs a much smaller distribution than Ubuntu. Ubuntu is going to be a few hundred megabytes however you slice it.

---

