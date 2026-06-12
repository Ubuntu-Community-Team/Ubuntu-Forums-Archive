---
title: "Check lib version"
date: 2010-02-02
forum: General Help
---

### Post by ABuNeNe on 2010-02-02
Hi, how do I check the version of a particular lib file as I' encounterd the following error:

```

/lib32/libc.so.6: version `GLIBC_2.11' not found (required by /lib32/libpng12.so.0)

```

Please advise. Thanks!

---

### Post by rnerwein on 2010-02-02
hi
got nearly the same problem with 32 bit libs. i guess you are running 9.10 64 bit mode ( next time don't forget to give some informations about the system you are running. ).
just call:
sudo apt-get install ia32-libs
sudo apt-get install gcc-4.4-multilib

this i think will solve your problem
ciao
 richi

---

### Post by ABuNeNe on 2010-02-02
> **rnerwein said:**
> hi
got nearly the same problem with 32 bit libs. i guess you are running 9.10 64 bit mode ( next time don't forget to give some informations about the system you are running. ).
just call:
sudo apt-get install ia32-libs
sudo apt-get install gcc-4.4-multilib

this i think will solve your problem
ciao
 richi

Hi rnerwein, I'm running Ubuntu 9.04 64 bits. I had [ia32-libs_2.7ubuntu18_amd64.deb]("http://ubuntu-archive.sit.kmutt.ac.th/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu18_amd64.deb") installed and I can't find the gcc-4.4-multilib which you've mentioned.

---

### Post by rnerwein on 2010-02-02
hi
sorry i don't know that you are running 9.04 but in 9.10 -->
root@tschang:~/tmp 09:16-> apt-cache search gcc-4.4-multilib
gcc-4.4-multilib - The GNU C compiler (multilib files)

it' present.
ciao

---

### Post by ABuNeNe on 2010-02-02
> **rnerwein said:**
> hi
sorry i don't know that you are running 9.04 but in 9.10 -->
root@tschang:~/tmp 09:16-> apt-cache search gcc-4.4-multilib
gcc-4.4-multilib - The GNU C compiler (multilib files)

it' present.
ciao

No worries. I use the command and found there is this gcc-4.3-multilib and it've been installed.

Any idea as I'm still having the /lib32/libc.so.6: version `GLIBC_2.11' not found (required by /lib32/libpng12.so.0) error.

---

