---
title: "is my system 64bit or 32 bit?"
date: 2010-01-26
forum: General Help
---

### Post by loki_dre on 2010-01-26
How do I find out if my computer is 64 bit or 32 bit?
I already have ubuntu installed.

---

### Post by bluefrog on 2010-01-26
uname -m

---

### Post by MarcDam on 2010-01-26
See [http://ubuntuforums.org/showthread.php?t=798907](http://ubuntuforums.org/showthread.php?t=798907)

---

### Post by oldos2er on 2010-01-26
> **loki_dre said:**
> How do I find out if my computer is 64 bit or 32 bit?
I already have ubuntu installed.

What CPU does your system have? The **uname -m** command will tell you if the kernel you're running is 32- or 64-bit; **cat /proc/cpuinfo** will give info on your CPU.

---

### Post by hhlp on 2010-01-26
this command will tell you the information you need

[PHP]lshw -C cpu[/PHP]

---

### Post by cariboo on 2010-01-26
I like using:

```
cat /proc/cpuinfo
```

it will tell you more than you need to know. :)

---

### Post by sisco311 on 2010-01-26
> **cariboo907 said:**
> I like using:

```
cat /proc/cpuinfo
```

it will tell you more than you need to know. :)

+1

The **lm** flag indicates that the CPU is a 64-bit proc. ;)

---

### Post by bodhi.zazen on 2010-01-26
> **sisco311 said:**
> +1

The **lm** flag indicates that the CPU is a 64-bit proc. ;)

To identify the version of Ubuntu, use

```
uname -m
```

To identify the CPU capabilities use

```
grep --color=always ' lm ' /proc/cpuinfo
```

If the second command gives any output , you have a 64 bit CPU,

If the second command gives no output you have a 32 bit CPU.

---

