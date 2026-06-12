---
title: "Unable to install Ubuntu 64 bit"
date: 2010-04-26
forum: General Help
---

### Post by sgsawant on 2010-04-26
I created a bootable USB using an iso file downloaded from ubuntu.com which reads:
ubuntu-9.10-desktop-amd64.iso

My processor is Intel core 2 duo t5750.

Unfortunately when I installed Ubuntu using the bootable USB, I think what I have installed right now is a 32-bit version of Ubuntu. How do I know? Well, I tried the "uname -a" command and it doesn't read "x86_64" anywhere! In fact it doesn't read 64 anywhere! Somewhere, after the command is executed, it reads "i686".

Can anyone guess what I did wrong? This is really bugging me. :confused:

Regards,

-sgsawant

---

### Post by rnerwein on 2010-04-26
hi
i have a amd - but try in a terminal window ( command line ) type:

lscpu

i think thats what's you are looking for.

ciao

---

### Post by 3rdalbum on 2010-04-26
I can't explain it - you've got the amd64 ISO on a flash drive, and when you used the installer there you ended off with the 32-bit edition? Beats me! Are you sure the drive didn't already have a 32-bit edition on it?

---

### Post by 3rdalbum on 2010-04-26
> **rnerwein said:**
> hi
i have a amd - but try in a terminal window ( command line ) type:

lscpu

More like:

```
cat /proc/cpuinfo
```

But that just tells you what sort of CPU you have, which you already know.

---

### Post by ssj6akshat on 2010-04-26
i686 is optimised for Pentium and later processors and AMD too(that includes dual core).i386 is optimised for older processors.
Bottom Line:It wouldn't show you x86_x64 but will show you i686 instead.

---

### Post by sgsawant on 2010-04-26
@ssj6akshat:

So what does i686 mean? Doesn't it definitely mean that my ubuntu is 32 bit? Are there computers with 64 bit ubuntu but on which the command "uname -a" doesn't yield x86_64?

@3rdalbum:

I still have the USB unchanged. How do I verify the version in my bootable USB is 32-bit or 64-bit?

Regards,

-sgsawant

---

### Post by 3rdalbum on 2010-04-26
> **ssj6akshat said:**
> i686 is optimised for Pentium and later processors and AMD too(that includes dual core).i386 is optimised for older processors.
Bottom Line:It wouldn't show you x86_x64 but will show you i686 instead.

But mine shows x86_64, not i686.

I have no idea how to tell if a flash drive has 64-bit or 32-bit on it apart from booting it up. My gut says you've got 32-bit on that flash drive, as it's reporting i686, but I don't actually know how you got 32-bit seemingly from a 64-bit ISO.

---

### Post by utnubuuser on 2010-04-26
Boot it on a 32 bit machine?

---

### Post by Axel-P on 2010-04-26
> **3rdalbum said:**
> But mine shows x86_64, not i686.

I have no idea how to tell if a flash drive has 64-bit or 32-bit on it apart from booting it up. My gut says you've got 32-bit on that flash drive, as it's reporting i686, but I don't actually know how you got 32-bit seemingly from a 64-bit ISO.

Well if it shows x86_64, you're ok ;) That means that you have a 64 bits installed. The history is this, technically if you had a 64 bit intel processor your architecture should be i686. But sometimes that's just not the case, don't know why:P

For example I have an intel core duo 64-bit, so technically my architecture should be i686. Well it is not. If I run uname -a it'll say a couple of things and at the end it will say: x86_64 GNU/Linux. So that means that I have a 64 bit architecture.


Same goes for sgsawant.

Type uname -a and at the end it should tell you what architecture you're using. If you ever find out that you have a 32 bit installation wipe out everything from that flash drive and make a new one. My advice: unetbootin, great software!

GL HF
Axel

---

