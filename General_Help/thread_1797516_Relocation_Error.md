---
title: "Relocation Error"
date: 2011-07-05
forum: General Help
---

### Post by Yargling on 2011-07-05
Hi,
 
I'm trying to run a program in Ubuntu (10.10), and I keep getting this error ([COLOR=black][FONT=Arial]relocation error: /lib/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference).[/FONT][/COLOR]
 
[COLOR=black][FONT=Arial]From what I've searched online, it has suggested that it can't locate 'strcmp' for version 2.0 of GLIBC; I also ran 'ldd' on the listed library and got:[/FONT][/COLOR]
 
[COLOR=black][FONT=Arial]> $ ldd -v /lib/libnss_files.so.2[/FONT][/COLOR]
[FONT=Arial]   [COLOR=black]linux-gate.so.1 => (0x00c9d000)[/COLOR][/FONT]
[FONT=Arial][COLOR=black]   libc.so.6 => /lib/libc.so.6 (0x00d67000)[/COLOR][/FONT]
[FONT=Arial][COLOR=black]   /lib/ld-linux.so.2 (0x00b39000)[/COLOR][/FONT]
[COLOR=black][FONT=Arial]Version information:[/FONT][/COLOR]
[FONT=Arial][COLOR=black]   /lib/libnss_files.so.2:[/COLOR][/FONT]
[FONT=Arial][COLOR=black]      libc.so.6 (GLIBC_2.1.3) => /lib/libc.so.6[/COLOR][/FONT]
[FONT=Arial][COLOR=black]      libc.so.6 (GLIBC_2.3) => /lib/libc.so.6[/COLOR][/FONT]
[FONT=Arial][COLOR=black]      libc.so.6 (GLIBC_2.1) => /lib/libc.so.6[/COLOR][/FONT]
[FONT=Arial][COLOR=black]      libc.so.6 (GLIBC_2.2) => /lib/libc.so.6[/COLOR][/FONT]
[FONT=Arial][COLOR=black]      libc.so.6 (GLIBC_PRIVATE) => /lib/libc.so.6[/COLOR][/FONT]
[FONT=Arial][COLOR=black]      libc.so.6 (GLIBC_2.0) => /lib/libc.so.6[/COLOR][/FONT]
[FONT=Arial][COLOR=black]   /lib/libc.so.6:[/COLOR][/FONT]
[FONT=Arial][COLOR=black]      ld-linux.so.2 (GLIBC_PRIVATE) => /lib/ld-linux.so.2[/COLOR][/FONT]
[FONT=Arial][COLOR=black]      ld-linux.so.2 (GLIBC_2.3) => /lib/ld-linux.so.2[/COLOR][/FONT]
[FONT=Arial][COLOR=black]      ld-linux.so.2 (GLIBC_2.1) => /lib/ld-linux.so.2[/COLOR][/FONT]
 
[COLOR=black][FONT=Arial]The section about /lib/libc.so.6 suggests to me that there is no mapped lib for GLIBC_2.0, and that is the source of the error.[/FONT][/COLOR]
 
[COLOR=black][FONT=Arial]Assuming I'm right, how do I fix that? I tried 'sudo ldconfig' by itself and that didn't seem to have any effect on the lib. [/FONT][/COLOR]
 
[COLOR=black][FONT=Arial]If I'm wrong, what else could it be?[/FONT][/COLOR]
 
[COLOR=black][FONT=Arial]Thanks in advance for your time.[/FONT][/COLOR]

---

### Post by Yargling on 2011-07-05
No idea's?

---

### Post by Yargling on 2011-07-05
Ok, I've been informed that the problem is due to changes from Libc-2.12.1.so from Libc-2.11.1.so - is there any way to force the version to 2.11.1? My Synaptic Package Manager doesn't appear to let me (it'll only allow version 2.12.1 variants).
 
If I need to downgrade my Linux box, please advise me to the version I'd need.
 
Thanks.

---

### Post by varunendra on 2011-07-05
> **Yargling said:**
> Ok, I've been informed that the problem is due to changes from Libc-2.12.1.so from Libc-2.11.1.so - is there any way to force the version to 2.11.1? My Synaptic Package Manager doesn't appear to let me (it'll only allow version 2.12.1 variants).
 
If I need to downgrade my Linux box, please advise me to the version I'd need.
 
Thanks.
While having no idea about your problem or its solution, you may try to switch to Ubuntu 10.04 which has this package in its repository.

Alternatively, you may add APT line:
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick mainto your 'Software Sources' list, then after reloading, search for **libc6** (mine is exactly **libc6-i686**).

But I've no idea what may happen if you try to force it on maverick. Maybe you can tell me later.. :)

---

### Post by wildmanne39 on 2011-07-05
> **Yargling said:**
> Ok, I've been informed that the problem is due to changes from Libc-2.12.1.so from Libc-2.11.1.so - is there any way to force the version to 2.11.1? My Synaptic Package Manager doesn't appear to let me (it'll only allow version 2.12.1 variants).
 
If I need to downgrade my Linux box, please advise me to the version I'd need.
 
Thanks.Hi, forcing usually breaks something important, like synaptic.

---

### Post by Yargling on 2011-07-07
Thanks for the information.
 
I have been able to get the software to work on a Ubuntu 10.04 virtual machine (with a temporary license from the supplier until they can fix it for Ubuntu 10.05+).

---

### Post by varunendra on 2011-07-07
> **Yargling said:**
> Thanks for the information.
 
I have been able to get the software to work on a Ubuntu 10.04 virtual machine (with a temporary license from the supplier until they can fix it for Ubuntu 10.05+).
Speaking of infos, 

ubuntu 10.04 = ubuntu released in 2010 - April (04)
ubuntu 10.10 = ubuntu released in 2010 - October (10)

It's not just a serial no., so no .05, .06.... only 04s and 10s (ubuntu releases twice an year - always in april and october).

-just yet another info :D

---

