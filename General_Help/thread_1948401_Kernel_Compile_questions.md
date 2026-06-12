---
title: "Kernel Compile questions"
date: 2012-03-28
forum: General Help
---

### Post by Binary-Synapse on 2012-03-28
Hello.
 
I have to apply a customized kernel in my laptop to allow for correct graphics support.
I have the kernel source code and I followed the instructions on 
[http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html)
to correctly apply the kernel.
Although old, those kernel compile instructions are still valid, right?
 
After everything is done (kernel compile+kernel install+initram creation+GRUB Update, etc...), when I reboot my system, my new /boot/initrd.img-3.0.0 file has 100MB!!
 
And my previous /boot/initrd.img-3.0.0-17-generic only has 14MB!
I guess the problem is when I execute "make menuconfig" command.
At that stage, multiple drivers are probably being loaded (by default).
 
So... the main questions are:
1-How can I reduce compile time (now it's taking 5 hours in a Netbook equipped with an Atom 1.6GHz CPU)?
 
2-What is the easiest way to reduce my initrd file size?
 
Thank you.

---

### Post by MG&amp;TL on 2012-03-28
1) How to reduce compile time. For a big compile, you can use the -j option to make to make your processor process more than one thread. Considering it's an intel Atom, I think 2 threads is about enough:

```
make -j2
```DO NOT just use make -j, this will execute a 'makebomb' freezing your system.

2) No definitive answer, just read up on what you do and don't need for your system. Why do you need to? 

Note: it might be helpful to read: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by Binary-Synapse on 2012-03-28
OK.
 
Nice tip.
 
And what about localmodconfig parameter?
 
Can I use that also?

---

### Post by MG&amp;TL on 2012-03-28
[http://www.h-online.com/open/features/Good-and-quick-kernel-configuration-creation-1403046.html](http://www.h-online.com/open/features/Good-and-quick-kernel-configuration-creation-1403046.html)
...it sounds good to me. :)

AFAIK, it's only one config file, so yes, use that and *make menuconfig* as well, if you like.

---

### Post by Doug S on 2012-03-28
I would definately recommend the reference that Mg&TL gave above ( [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) ).
There are links within that reference for specific examples that are also good.
I found the various number of threads arguments didn't make any difference, it seemed to be multithreaded anyhow.
Only 5 hours! On my pathetic old server it took over 33 hours, and then it gave up with an out of memory error. My new server takes 13 minutes.
 
If I am workig on just one file and re-compiling, I am used to large build environments where I only have to re-compile that one program or module and then re-link the whole thing. I have not figured out how to do that with the kernel. That could possibly save a lot of time.
 
I have no clue about your other questions.

---

### Post by MG&amp;TL on 2012-03-28
> **Doug S said:**
> 
I found the various number of threads arguments didn't make any difference, it seemed to be multithreaded anyhow.


Probably, the kernel has its own way of doing everything. I just assumed it would work, as I usually use that for *make* on general programs, it works a dream for compiling latest version of Unity. :)

---

### Post by Binary-Synapse on 2012-03-28
> **Doug S said:**
> On my pathetic old server it took over 33 hours, and then it gave up with an out of memory error. My new server takes 13 minutes.
 
Jesus!
 
And I thought 5 hours was long...

---

### Post by MG&amp;TL on 2012-03-28
> **Binary-Synapse said:**
> Jesus!
 
And I thought 5 hours was long...

Yeah, whatever you do, don't do it in VirtualBox-that's a two-day job too.

---

