---
title: "install: cannot stat `/.../tools/hv/*.8': No such file or directory"
date: 2012-04-16
forum: General Help
---

### Post by masuch on 2012-04-16
Hi,

I have compiled kernel 3.3.2 64 bit wih ubuntu patches and got error:

install: cannot stat `/home/u1/Kernel_3.3.2/linux-3.3.2/tools/hv/*.8': No such file or directory
make: *** [install-tools] Error 1

It came from .../debian/rules.d/3-binary-indep.mk line 116

I have cheked the directory and there is no *.8 file but only hv_kvp_daemon.c .

Could please anybody help me - is it my mistake within compilation process ? May I ignore it ? If not should I report it and where ?

Thank you for any clue.
Regards,
M

---

### Post by gordintoronto on 2012-04-16
> **masuch said:**
> I have compiled kernel 3.3.2 64 bit wih ubuntu patches....

It has been four hours, and you have no responses.

I can't imagine a bigger waste of time than compiling the 3.3.2 kernel.

Even so, good luck.

---

### Post by masuch on 2012-04-17
> **gordintoronto said:**
> It has been four hours, and you have no responses.

I can't imagine a bigger waste of time than compiling the 3.3.2 kernel.

Even so, good luck.

I cannot image bigger nonsense than you said. It has always been reliable and trustworthy to give strict answer without explanation - are you boss ? 
(one of my reasons is sas driver for Revodrive 3 PCI-E - which is not yet officialy supported by oneiric ubuntu kernels). At this moment I am running on 3.3.1 but 3.3.2 not successully compiled - strange to me :-)

---

### Post by didistortion on 2012-04-17
I had the same issue as you. Just comment out line 116 of the file you mentioned and the kernel builds just fine.

---

### Post by masuch on 2012-04-18
> **didistortion said:**
> I had the same issue as you. Just comment out line 116 of the file you mentioned and the kernel builds just fine.

OK, thanks. I compared 3-binary-indep.mk 3.3.2 with 3.3.1 and it is missing in 3.3.1

SOLVED.

---

