---
title: "Compiled Kernel Compatibilty among Distros"
date: 2011-07-22
forum: General Help
---

### Post by JASONFUSARO on 2011-07-22
Good morning everyone

jason@UbuntuStudio64bit:~$ uname -a
Linux UbuntuStudio64bit**[COLOR=Red] 3.0.0 [/COLOR]**#1 SMP Fri Jul 22 03:05:50 EDT 2011 x86_64 x86_64 x86_64 GNU/Linux

I recently compiled the 3.0.0 kernel and am trying to determine if I have to compile in each distro or if some steps can be bypassed according to which distro I wish to use the newly compiled kernel.

I went from vmlinuz-2.6.38-8-generic to vmlinuz-2.6.38-10-generic and then noticed on a thread that 3.0.0 was released and decided to compile it, which I am now using.

I have a few questions regarding this newly compiled kernel and its compatibility across multiple Distros.

This would achieve not having to install the required software ie gcc, binutils, etcc which are required to compile in that particular distro.

Q#1)

Can I call ie.(use) the kernel I have compiled ie. 3.0.0 in all installed Distros or do I have to run each distro and compile it there?


Q#2)

If I can then can I also just copy lib/modules/<NEW KERNEL VERSION> from the working distro to each of those Distros or do I have to run make modules in each?


Q#3)

If debian can I use the system.map-3.0.0 and initramfs-3.0.0 from the current ubuntu and for other Distros just create them in the particular distro, and initrd I can just recreate them in that distro.



Q#4)

If I have to compile in each distro then can I use the .config from this distro which only pertains to my current hardware and system requirements and would not change irregardless of the distro I was running.



I apologize if the number of questions are too many for one thread. I realize that I could probably track down an answer (maybe) through searches but I figure someone with a great deal of experience in kernel compiling could shorten the time to answer my questions.

Thank you

---

### Post by dino99 on 2011-07-22
each kernel is already compiled into repo, watch synaptic

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)


mostly all distro have such features. And to answer your questions: each distro have specific settings, so dont mix the whole thing, except if uou like breakages and debugging of course :)

---

### Post by JASONFUSARO on 2011-07-22
> **dino99 said:**
> each kernel is already compiled into repo, watch synaptic

[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")


mostly all distro have such features. And to answer your questions: each distro have specific settings, so dont mix the whole thing, except if uou like breakages and debugging of course :)


But that is with generic options, I modifed my options using make xconfig, like selecting core 2, and deslecting other options, I thought that was the point of compiling the kernel yourself to get rid of what is not needed?

---

### Post by JASONFUSARO on 2011-07-22
The following answered my question

[http://unixbhaskar.wordpress.com/2010/02/17/compiling-custom-kernel-for-different-gnulinux-distributions/](http://unixbhaskar.wordpress.com/2010/02/17/compiling-custom-kernel-for-different-gnulinux-distributions/)

---

