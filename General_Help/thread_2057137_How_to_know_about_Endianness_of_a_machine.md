---
title: "How to know about Endianness of a machine"
date: 2012-09-13
forum: General Help
---

### Post by Ankita Singlaa on 2012-09-13
hi 

I have a ubuntu machine and **want to know the endianness of the system**....
How would i get to know.....

The information of my machine is: 

```
uname -a
```

42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 201
1 i686 i686 i386 GNU/Linux

and 

```
lsb_release -a
```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 11.04
Release:        11.04
Codename:       natty
root@cloudx-538-520:~#
root@cloudx-538-520:~#

I have done it using C Program......but **dont want to know using C Program**.......
**Want some linux command to know endianness of a machine**

Plzz Help...
Thanks in advance....

---

### Post by plucky on 2012-09-13
**endianness**

Please translate,that is not an English word that I have ever heard.

---

### Post by Statia on 2012-09-13
> **plucky said:**
> **endianness**

Please translate,that is not an English word that I have ever heard.


[http://en.wikipedia.org/wiki/Endianness](http://en.wikipedia.org/wiki/Endianness)

---

### Post by Vaphell on 2012-09-13
the list of little-endian and big-endian architectures is rather fixed, just read wiki

[http://en.wikipedia.org/wiki/Endianness#Endianness_and_operating_systems_on_architectures](http://en.wikipedia.org/wiki/Endianness#Endianness_and_operating_systems_on_architectures)

---

### Post by Statia on 2012-09-13
> **Ankita Singlaa said:**
> 

```
uname -a
```42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 201
1 i686 i686 i386 GNU/Linux


If your system is x86, it is little-endian.
I don't know if there is a command that will tell you this.
I could imagine that it might get checked when you do a ./configure before compiling something, so browse around some configure scripts.

---

### Post by decrepit on 2012-09-13
> **plucky said:**
> **endianness**

Please translate,that is not an English word that I have ever heard.

I hadn't heard about it either, but wikipedia has a page on it.

> Endianness
From Wikipedia, the free encyclopedia
Jump to: navigation, search
"Endian" redirects here. For the Linux routing and firewall distribution, see Endian Firewall. For Jonathan Swift's Big-Endian and Little-Endian parties in Lilliput, see Lilliput and Blefuscu.

In computing, the term endian or endianness refers to the ordering of individually addressable sub-components within the representation of a larger data item as stored in external memory (or, sometimes, as sent on a serial connection). Each sub-component in the representation has a unique degree of significance, like the place value of digits in a decimal number. These sub-components are typically 16-, 32- or 64-bit words, 8-bit bytes, or even bits. Endianness is a difference in data representation at the hardware level and may or may not be transparent at higher levels, depending on factors such as the type of high level language used.

---

