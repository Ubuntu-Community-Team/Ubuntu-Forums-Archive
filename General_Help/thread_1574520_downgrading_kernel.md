---
title: "downgrading kernel"
date: 2010-09-14
forum: General Help
---

### Post by Pacopag on 2010-09-14
Hi.  I'm having compatibility issues with a program I need to use.  I'm told that downgrading to kernel 2.6.30 will fix the problem.  I would just like to know if the instructions at this site are good

[http://linuxd.wordpress.com/2008/11/26/how-to-downgrade-the-kernel-in-ubuntu-810-the-easy-way/](http://linuxd.wordpress.com/2008/11/26/how-to-downgrade-the-kernel-in-ubuntu-810-the-easy-way/)

I really don't want to break my system because I've installed about 10 different distros lately, and I'd rather not have to do it again.

Also, I was wondering what effect downgrading the kernel will have on my system.

Thanks very much,

---

### Post by drpjkurian on 2010-09-14
Hi
You can select older Kernel while booting. During booting, you can select the appropriate kernel in the GRUB menu. This will solve your kernel issues

---

### Post by andrewthomas on 2010-09-14
What version of Ubuntu are you running?

---

### Post by Pacopag on 2010-09-14
I'm running a fresh install of Ubuntu 10.04.  I don't think I get an option for older kernel, but I'll check.

---

### Post by Pacopag on 2010-09-14
There's only one kernel option at startup.

---

### Post by snowpine on 2010-09-14
Since 2.6.32 is the one (and only) supported kernel for Ubuntu 10.04, let's back up a moment and analyze this statement:

> **Pacopag said:**
> HI'm having compatibility issues with a program I need to use.  I'm told that downgrading to kernel 2.6.30 will fix the problem. 

What is the program? What are the compatibility issues? Who told you a downgrade to 2.6.30 will fix the issue, and why?

> **Pacopag said:**
> I would just like to know if the instructions at this site are good

[http://linuxd.wordpress.com/2008/11/26/how-to-downgrade-the-kernel-in-ubuntu-810-the-easy-way/](http://linuxd.wordpress.com/2008/11/26/how-to-downgrade-the-kernel-in-ubuntu-810-the-easy-way/)

You are not using Ubuntu 8.10.

> **Pacopag said:**
> Also, I was wondering what effect downgrading the kernel will have on my system.

The kernel is the most important part of Linux and downgrading it may have a huge effect.

[http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)

---

### Post by Pacopag on 2010-09-14
The program is Mathematica 6.  I got an error during the installation, and their support team told me about the compatibility issue and to downgrade the kernel.  The other option was to upgrade to Mathematica 7, but that will cost more money than I would like to spend.  What other options do I have?

---

### Post by snowpine on 2010-09-14
> **Pacopag said:**
> The program is Mathematica 6.  I got an error during the installation, and their support team told me about the compatibility issue and to downgrade the kernel.  The other option was to upgrade to Mathematica 7, but that will cost more money than I would like to spend.  What other options do I have?

I am not familiar with Mathematica and unfortunately cannot help you troubleshoot. :(

All Ubuntu kernels (including 2.6.30) [are available here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"). They are .deb files so all you need to do is download and double-click the correct linux-image for your architecture. You are free to experiment with them at your own risk; you would gain Mathematica support but lose Ubuntu support, so it is up to you to decide which is more important. :)

---

### Post by Pacopag on 2010-09-14
Well, that's ok.  I think Ubuntu support is more important.  I'll call Mathematica and see what it'll cost to upgrade my license.  Thanks again.

Cheers,

---

### Post by pbrane on 2010-09-14
What errors do you see if you run the Mathematica install from the terminal? What is the error you are getting? Are you sure this is not a library compatibility issue? I'm not sure what in the kernel would cause a user app not to run.

---

### Post by Pacopag on 2010-09-14
I get almost to the end of the install, then it says "Installation failed" and tells me to look at an error file.  There are the contents of the error file

/usr/local/Wolfram/Mathematica/6.0/SystemFiles/Kernel/Binaries/Linux-x86-64/MathKernel: Symbol `__kmp_test_then_add_real32' causes overflow in R_X86_64_PC32 relocation
/usr/local/Wolfram/Mathematica/6.0/SystemFiles/Kernel/Binaries/Linux-x86-64/MathKernel: Symbol `__kmp_test_then_add_real64' causes overflow in R_X86_64_PC32 relocation
/usr/local/Wolfram/Mathematica/6.0/SystemFiles/Kernel/Binaries/Linux-x86-64/MathKernel: Symbol `__kmp_test_then_add_real32' causes overflow in R_X86_64_PC32 relocation
/usr/local/Wolfram/Mathematica/6.0/SystemFiles/Kernel/Binaries/Linux-x86-64/MathKernel: Symbol `__kmp_test_then_add_real64' causes overflow in R_X86_64_PC32 relocation

---

### Post by snowpine on 2010-09-14
I should add there is no *risk* to trying a different kernel. If you don't like it, you can select your previous kernel from the GRUB boot menu and continue business as usual. So it may be worth experimenting before shelling out the money for an upgrade. :)

---

### Post by pbrane on 2010-09-14
Have you tried running Mathematica? Others have gotten these errors and say it runs fine.

---

### Post by Pacopag on 2010-09-14
actually it does work!  Thanks.  I can't believe I didn't even try it.  I guess I'll just use it like this.

---

