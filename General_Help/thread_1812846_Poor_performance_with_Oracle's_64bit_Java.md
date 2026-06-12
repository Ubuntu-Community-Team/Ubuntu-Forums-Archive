---
title: "Poor performance with Oracle's 64bit Java"
date: 2011-07-26
forum: General Help
---

### Post by gabriel.poesia on 2011-07-26
Hi there, nice to meet you all :)

First of all, thanks for the attention.

I'm having a really weird performance issue with Java in 64bit. I'm a Grails developer, and I am trying to run IntelliJ IDEA on a Kubuntu 11.04 in my HP Pavilion dv6 laptop.

The strange facts are: if I run the same program on a Ubuntu 11.04 32 bit in my desktop, and it performs really smoothly. If I run it (same JDK/JRE version, but 64 bit) here on the laptop, it performs really badly, and it's completely unusable. Most times, after like 5 minutes of use, it freezes. Under Windows, it works flawlessy (wasn't Java's slogan "write once, run anywhere" sometime ago? :P): .

The problem is not restricted to IntelliJ IDEA, though. Eclipse is also slow (although much better than IDEA). So that's what makes me think it's Java in general.

In the desktop, I have 2 GB of RAM (IDEA uses almost 1GB). Here in the  laptop, I have 4GB of RAM. So that shouldn't be the problem, right? I  use no swap space here, because in the desktop it's never used (that's  what the System Monitor shows me).

The processors in both machines are nearly equivalent. I have an Intel  Core 2 Duo in the Desktop, and an AMD Phenon II Quad-Core P920 in the  laptop.

Any clues?

Thanks in advance.

---

### Post by gabriel.poesia on 2011-07-28
I created a swap file of 2GB, and it incredibly enhanced Java's performance. Although it can still get a bit better (compared to the desktop), I think creating a swap partition will solve this (as it's generally faster than a swap file, provided that it's contiguous space).

So I'm marking this as solved.

Thanks!

---

