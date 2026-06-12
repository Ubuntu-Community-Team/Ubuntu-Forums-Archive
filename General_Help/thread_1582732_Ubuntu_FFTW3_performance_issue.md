---
title: "Ubuntu FFTW3 performance issue"
date: 2010-09-26
forum: General Help
---

### Post by Pev on 2010-09-26
Hi,

I'm currently moving a computer (old Opteron) from a old version of Gentoo 2.6.12-gentoo-r6 to Ubuntu 10.04.1 Server amd64 (2.6.32-24-server).

However I have hit an issue regarding the performance of a piece of complied software. This software greatly users the FFTW3 libary. So I compiled FFTW from source with SSE (I only care about float) and got a significant performance improvement. However it's still consuming more then double the amount of CPU resources as the Gentoo variant.

The Gentoo FFTW3 was version 3.0.1. The Ubuntu is using version 3.2.2.

Is there something I can do to improve performance. Would kernal customisation help (can you point me to a resource).

I don't expect to reach parity between the two distros but I need to reduce the CPU load on the Ubuntu version down by a third (it's currently %55).

Thanks,

---

### Post by Pev on 2010-10-04
... Anyone?

I just need to improve Ubuntu's numerical performance. Would a custom kernel achieve this or would it be more trouble then it's worth?

---

### Post by Pev on 2010-10-04
I've just notice that the majority of the extra load CPU load is all coming form the system/kernel (sy field in top). 

Could there be some security process which is intercepting the kernel calls? Does anyone know a way I can profile the system to find out?

---

