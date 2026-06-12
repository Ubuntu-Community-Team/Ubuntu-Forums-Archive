---
title: "No Such file or directory"
date: 2011-12-24
forum: General Help
---

### Post by princebadshah on 2011-12-24
Hello 

 I  stuck with very strange error in ubuntu but very naive
 
 root@ubuntu:/opt/nios2/bin# ls
 nios2-linux-ld.real    nios2-linux-uclibc-gcc        tclsh8.4
 nios2-linux-nm         nios2-linux-uclibc-gcc-3.4.6  wish8.
 
 root@ubuntu:/opt/nios2/bin# nios2-linux-uclibc-gcc -v
 bash: /opt/nios2/bin/nios2-linux-uclibc-gcc: No such file or directory
 
 root@ubuntu:/home/ramzan/nios2-linux# echo $PATH
 /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/nios2/bin

Thanks for your help

---

### Post by Vaphell on 2011-12-24
maybe it's a 32bit vs 64bit issue?
```
uname -m
file /opt/nios2/bin/nios2-linux-uclibc-gcc
```

---

### Post by bobsageek on 2011-12-24
Output of ```
ls -al | grep nios2-linux-uclibc-gcc
``` please?

---

### Post by Lampi on 2011-12-24
it's
```
root@ubuntu:/opt/nios2/bin# ./nios2-linux-uclibc-gcc -v
```
notice ./ before the command - only necessary if you run it from the same dir you're in.

---

### Post by princebadshah on 2011-12-24
> **Vaphell said:**
> maybe it's a 32bit vs 64bit issue?
```
uname -m
file /opt/nios2/bin/nios2-linux-uclibc-gcc
```


root@ubuntu:/home/ramzan# nios2-linux-uclibc-gcc -v
bash: /opt/nios2/bin/nios2-linux-uclibc-gcc: No such file or directory
root@ubuntu:/home/ramzan# uname -m
x86_64
root@ubuntu:/home/ramzan# file /opt/nios2/bin/nios2-linux-uclibc-gcc
/opt/nios2/bin/nios2-linux-uclibc-gcc: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.5, stripped


So what to do now ?

---

### Post by princebadshah on 2011-12-24
> **bobsageek said:**
> Output of ```
ls -al | grep nios2-linux-uclibc-gcc
``` please?

root@ubuntu:/home/ramzan# ls -al | grep nios2-linux-uclibc-gcc
ls: cannot access .gvfs: Permission denied

---

### Post by princebadshah on 2011-12-24
> **Lampi said:**
> it's
```
root@ubuntu:/opt/nios2/bin# ./nios2-linux-uclibc-gcc -v
```notice ./ before the command - only necessary if you run it from the same dir you're in.

root@ubuntu:/opt/nios2/bin# ./nios2-linux-uclibc-gcc -v
bash: ./nios2-linux-uclibc-gcc: No such file or directory

---

### Post by WorMzy on 2011-12-24
> **princebadshah said:**
> root@ubuntu:/home/ramzan# nios2-linux-uclibc-gcc -v
bash: /opt/nios2/bin/nios2-linux-uclibc-gcc: No such file or directory
root@ubuntu:/home/ramzan# uname -m
x86_64
root@ubuntu:/home/ramzan# file /opt/nios2/bin/nios2-linux-uclibc-gcc
/opt/nios2/bin/nios2-linux-uclibc-gcc: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.5, stripped


So what to do now ?

That's a 32-bit executable, and you're running a 64-bit operating system.

I suggest that you download the 64-bit version of whatever this application is, or else install the 32-bit versions of the libraries it needs to run.

---

### Post by princebadshah on 2011-12-24
Thanksss alot guys,
This is ulinuc , LINUX for FPGA,  I installed ubuntu on my system but my Windows 7 tells me that it is32 bit OS. So is it possible I can install ubuntu 32 bit .
I am sorry for really basic question ...

---

### Post by WorMzy on 2011-12-24
You can have both 32-bit and 64-bit operating systems on a 64-bit capable PC. If Ubuntu is able to boot the 64-bit kernel, then your PC is 64-bit capable. If Windows is 32-bit, that just means that Windows is 32-bit, it doesn't meant the PC is. :)

If you want to install the 32-bit version of Ubuntu, you can download it from the same place you can get the 64-bit version ([here](http://www.ubuntu.com/download/ubuntu/download)).

You can't convert a 64-bit installation into a 32-bit installation, so you'll need to completely reinstall Ubuntu to get the 32-bit version.

But, like I said, you can run 32-bit applications on 64-bit operating systems, so long as you have the 32-bit versions of the libraries that the application uses. There's no need to reinstall the entire operating system to run one application.

---

