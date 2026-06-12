---
title: "Debootstrap --arch parameter bugging"
date: 2010-02-11
forum: General Help
---

### Post by shea279 on 2010-02-11
OK, so I am trying to use debootstrap to download a copy of 32 bit karmic to a folder, so I can chroot into it, however it is not working. (the host machine is x64)

I use the command
```
debootstrap --arch i386 karmic folder
```
then after it downloads:
```
sudo chroot folder
uname -a

```
and it spits out
```
Linux xaphan 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
```

Why does it appear to be a x86_64 bit build of linux, even though I downloaded the i386 version of it using debootstrap?!?

---

### Post by sisco311 on 2010-02-11
> **shea279 said:**
> 
```
Linux xaphan 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
```

Why does it appear to be a x86_64 bit build of linux, even though I downloaded the i386 version of it using debootstrap?!?

You run the 32bit environment on top of the 64bit kernel.

uname prints the architecture of the host kernel.

i.e., here is the output of uname -a from my chroot:
```
sisco@acme:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	**Ubuntu**
Description:	Ubuntu lucid (development branch)
Release:	10.04
Codename:	lucid
sisco@acme:~$ uname -a
Linux acme **2.6.32-ARCH** #1 SMP PREEMPT Fri Jan 29 09:10:49 CET 2010 x86_64 GNU/Linux

```
as you can see, uname prints the release name of my ArchLinux kernel.

---

