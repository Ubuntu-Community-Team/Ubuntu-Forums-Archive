---
title: "Ubuntu 10.10 vs. kernel 2.6.29"
date: 2011-03-15
forum: General Help
---

### Post by GABIKA6 on 2011-03-15
Hi!

I am using linux ubuntu 10.10 (32-bit) since some days, so I am a noob user.

I placed Ubuntu on the same drive as my windows XP is, and there were no problems, everything was fine, all drivers were working...
I need to use kernel 2.6.29 and i read about "how to install a new kernel" on this forum. I downloaded 3 files, I installed them in a good sequence. After reboot I can choose between 3 kernels, and if I choose this, then there is a mounting problem:

mounting none on /dev failed

Afterthat there is written something else, what I cant read. Some seconds later ubuntu boots, but my (non-USB) mouse isnt working.

Waiting for your reply

---

### Post by uRock on 2011-03-15
Hello and welcome,

Is there a reason that you need that old kernel?

---

### Post by GABIKA6 on 2011-03-15
> **uRock said:**
> Hello and welcome,

Is there a reason that you need that old kernel?

Yeah. I need to make an IPv6 Home Agent, and this kernel is supported, I read it on [http://www.nautilus6.org/doc/nepl-howto/nepl-howto.html](http://www.nautilus6.org/doc/nepl-howto/nepl-howto.html) site. I read it, that I have to use this version of kernel, because I have to rewrite the kernel, and the steps written on the nautilus site only work on this (I dont know why).

---

### Post by khelben1979 on 2011-03-15
Are you experienced enough to compile your own Linux kernel?

[KernelCompile - Ubuntuforums.org]("https://help.ubuntu.com/community/Kernel/Compile").

---

### Post by GABIKA6 on 2011-03-15
I am not experienced enough yet, but i saw that, on this page there was written step-by-step what to change, and maybe I will google a lot :D most of the people I talk to and use linux, are asking that "am I enough good to do this..." I hope I will be.

First step, that I need to boot through this kernel.

---

### Post by lithopsian on 2011-03-15
I think you have very little chance of getting that kernel working with Ubuntu 10.10.

The instructions given are specific to the 2.6.29 kernel but they will work equally well with later kernels. A few of the options may have different names, perhaps even some have been removed as they are permanently built in.  I haven't looked at the 2.6.35 kernel, but most of those options will already be selected by default.  Just double-check, switch on the ones that aren't already and rebuild it.   Start from the config for your existing Ubuntu kernel, not from the default that comes with the source download.  You could even examine the config file for your current kernel and if you're very lucky you might be able to find all the options already enabled.

---

### Post by GABIKA6 on 2011-03-15
Can you tell me where can I find a document, that tells me which version of ubuntu will work completly with this kernel?

---

### Post by khelben1979 on 2011-03-16
[Ubuntu Intrepid]("http://en.wikipedia.org/wiki/Ubuntu_intrepid#Ubuntu_8.10_.28Intrepid_Ibex.29") got kernel 2.6.28 and so it might be a better idea to try with this version of Ubuntu.

---

### Post by GABIKA6 on 2011-06-02
Actually it works fine with ubuntu 11.04 too, the only question is now that the userland umip support will be good enough for the newest ubuntu distribution aswell.

---

