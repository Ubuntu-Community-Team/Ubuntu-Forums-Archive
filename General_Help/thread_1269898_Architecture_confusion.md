---
title: "Architecture confusion"
date: 2009-09-18
forum: General Help
---

### Post by spiritofcat on 2009-09-18
I recently bought this PC with Ubuntu already installed on it.
I was told the processor was a Celeron D 2.8GHz.

I was trying to install a program today using checkinstall and I was surprised to find it was defaulting to AMD64 as the architecture when creating the package.
As far as I am aware, a Celeron D 2.8GHz is an Intel 32Bit processor.

I tried the command [COLOR=DarkRed]uname -m[/COLOR][COLOR=Black] and it returned x86_64.

However, when I tried entering x86_64 as the architecture in checkinstall it failed to install and said that was the wrong architecture.
Using AMD64 it installed without any problem.

So I'm a bit confused about all this.
Is my CPU AMD or Intel? Is it 32 or 64 Bit?
[/COLOR]

---

### Post by skatinjj on 2009-09-18
My AMD Sempron returns the same output using that command

---

### Post by anystupidname1 on 2009-09-18
try
> cat /proc/cpuinfo | grep model

---

### Post by spiritofcat on 2009-09-19
Okay, tried cat /proc/cpuinfo | grep model
> model        : 4
model name    : Intel(R) Celeron(R) CPU 2.80GHz


So it definitely is an Intel Celeron 2.80GHz, but is it 32 or 64 bit?
And why does checkinstall insinst that it is AMD?

---

### Post by anystupidname1 on 2009-09-26
64bit processors have the "lm" flag

---

