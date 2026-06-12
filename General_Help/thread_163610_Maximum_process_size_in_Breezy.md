---
title: "Maximum process size in Breezy?"
date: 2006-04-21
forum: General Help
---

### Post by outofsync on 2006-04-21
Hi,

I'm having problems with an application that needs a lot of memory (a command-line solver for sparse matrices). I've allocated a 2GB swap file, and enabled it, so it's listed when I do 'swapon -s'.

In total, now I have 512MB RAM, plus 256MB swappartition, plus 2GB swapfile (ie: about 2.7GB)

The process stops because an allocation of 1.2GB fails (calloc returns NULL). I don't know how much memory is the process already using when that allocation is tried.

However, before I research more... I'm using the x86 version of Breezy, so I guess it's a 32bit kernel... what's the maximum size a process can get with this kernel?

I remember WindowsXP Home has a limit of 2GB...  does Breezy also have this limit?

Is there anyway for raising it?

Thanks!

---

### Post by outofsync on 2006-04-21
After continuing my search, still didn't find any previous discussion of this topic, but I found that RedHat seems to have a kernel called "hugemem" which supports processes of up to 4GB on x86.

In the Ubuntu forums, I found a perhaps related topic which suggests to install the "linux-image-686" package... but I'm not sure if that can be a dangerous move, considering that I installed the accelerated ATI drivers, and I remember I needed to install the i386 kernel headers for compiling the driver... could I break this system if I install the 686 kernel on it?

---

### Post by outofsync on 2006-04-21
No way, installed the 686 kernel (uname -a reports it), but the application can't allocate 1.2GB (my current available memory is 512MB physical, plus 2.2GB swap).

Do you know if the max process size in all Ubuntu kernels is 1GB? It looks like that.

---

