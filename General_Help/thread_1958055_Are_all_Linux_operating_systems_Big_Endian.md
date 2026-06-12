---
title: "Are all Linux operating systems Big Endian?"
date: 2012-04-13
forum: General Help
---

### Post by deleyd on 2012-04-13
My understanding is Microsoft Windows is Little Endian, Unix/Linux (including Ubuntu) is Big Endian.

However, I have Ubuntu as a dual-boot option on my Microsoft Windows laptop, which uses a Little Endian CPU. So I'm starting to wonder, is it the operating system which determines the "endianness", or the CPU?

---

### Post by cprofitt on 2012-04-13
From my understanding its the CPU that determines that...

see more: [http://en.wikipedia.org/wiki/Endianness](http://en.wikipedia.org/wiki/Endianness)

---

### Post by 3Miro on 2012-04-13
The endian is a property of the CPU not the OS. An operating system can be ported to work on many hardware architectures, which means that an OS can work on different endians.

All Intel and AMD CPUs of x86/amd64 type have the same endian. Both Windows and the versions of Linux designed for those CPUs (such as Ubuntu and Fedora) have the same endian. Linux in general has been ported on many other CPU architectures, including architectures with different endian (i.e. the old Mac PowerPC processors).

---

### Post by jadtech on 2012-04-13
big endian/ little endian 

has to do with how memory is stored/handled (formats)

each byte of memory has bits stored within it each bit has an address(index) this goes for all memory be it ram. HD. cpu  and so on 64bit has 4 bits per byte when the most significant bit of 4 bits get the most insignificant address this is big endianess, reversed would be small endianess.. 

this is in it most simplistic form

---

### Post by jadtech on 2012-04-13
to answer the question Windows is little endian mostly, linux  is both big and small (little) it runs on many architectures..

---

### Post by dcstar on 2012-04-13
> **deleyd said:**
> 
.........
So I'm starting to wonder, is it the operating system which determines the "endianness", or the CPU?

Start writing machine code for the CPU hardware you are using and you will soon find out the answer.

---

