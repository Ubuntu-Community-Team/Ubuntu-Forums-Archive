---
title: "patch kernel for vaio support"
date: 2011-05-14
forum: General Help
---

### Post by rodamu on 2011-05-14
Hi, my name is Rodrigo, and I've been using ubuntu since 2 weeks, but know about it since Ubuntu's 7.04 release. I originally installed Ubuntu 10.10 in my notebook, but many things didn't work out-of-the-box, so I decided to drop it. But recently, as in the university I am requierd to use Linux for programming, I had to install Linux again. This time everything worked out of the box. Exept some things like keyboard backlight, ambient light sensor, fingerprint reader, fn keys, etc. The thing is that I found a project which aims to fully support VAIO hardware in Linux.

My model is VPCS120FL, and it's supposed to work with that project. The problem now is that I'm required to patch the kernel. How can I do that?

The project url: [http://code.google.com/p/vaio-f11-linux/](http://code.google.com/p/vaio-f11-linux/)

Installing HOWTO: [http://code.google.com/p/vaio-f11-linux/wiki/KernelSupport](http://code.google.com/p/vaio-f11-linux/wiki/KernelSupport)

I try to do what the HOWTO says, but I can't manage to patch my kernel.

PS: If someone who has a VAIO could give me a hand instaling these modules I would appreciate that!

Thanks in advance

---

### Post by lithopsian on 2011-05-14
To "patch" a kernel, you have to compile the kernel.  I'm guessing you've never compiled a kernel?  You should probably make sure you can copmile the kernel before you start trying to patch it.

First get your kernel source and unpack it in /usr/src.  Symlink /usr/src/linux to your source directory.  So now when you download your patch with the command given, it will change some of your source files.

Now go into /usr/src/linux and do the make menuconfig command.  This is the most horrible way to change the kernel configuration, but you only have to change one line.  Fine the SONY_LAPTOP line and set it to Y.

Now you have to compile the kernel.  That is the command with all the makes in it.  I suggest you execute each one separately instead of all in a big line, so you can see what is going on.

Report errors here.  There is likely to be all sorts of missing tools packages, etc. that you need.

---

### Post by rodamu on 2011-05-14
this may sound veeery stupid, but what should i do with the kernel? I donload one from the web or i copy my kernel to that folder?

---

### Post by lithopsian on 2011-05-14
[2.6.39 kernel source](http://www.kernel.org/pub/linux/kernel/v2.6/testing/linux-2.6.39-rc7.tar.bz2).  Download and unpack.  It's big!  And you'll need a lot of space when you compile, although the final kernel is only a few meg, plus maybe 100MB of modules.

---

### Post by rodamu on 2011-05-14
I already downloaded the kernel, but i see that it's a release candidate. Is it better to use the rc or the stable? do you think it's stable enough?

---

### Post by lithopsian on 2011-05-14
Download whichever kernel you want, there are hundreds of them.  The latest stable is 2.6.38.6.  I think you're getting caught up in needless details at this point.  Download something and get it to compile.  Then you can download dozens of kernels and do whatever you like with them, but you're a long way from that stage.

---

### Post by rodamu on 2011-05-14
Sorry, I need to be completly sure that what I'm going to do won't **** up my system. I already fked 2 linux instalations this week :P

Ok, I downloaded the stable kernel and I patched. the .39 gave me an error so I tried the .38. It patched correctly.

Now I'm prompt to configure the kernel. Goddam now I really don't know what to do!! haha

Any ideas on where the "CONFIG_SONY_LAPTOP=y" is?

thanks in advance I really appreciate what you are doing to help me ;)

---

### Post by rodamu on 2011-05-14
Aditional data:

I managed to search what the HOWTO says:

> &#9474; Symbol: SONY_LAPTOP [=m]                                                                                                                                        &#9474;  
  &#9474; Type  : tristate                                                                                                                                                &#9474;  
  &#9474; Prompt: Sony Laptop Extras                                                                                                                                      &#9474;  
  &#9474;   Defined at drivers/platform/x86/Kconfig:205                                                                                                                   &#9474;  
  &#9474;   Depends on: X86 [=y] && X86_PLATFORM_DEVICES [=y] && ACPI [=y] && INPUT [=y] && RFKILL [=y]                                                                   &#9474;  
  &#9474;   Location:                                                                                                                                                     &#9474;  
  &#9474;     -> Device Drivers                                                                                                                                           &#9474;  
  &#9474;       -> X86 Platform Specific Device Drivers (X86_PLATFORM_DEVICES [=y])                                                                                       &#9474;  
  &#9474;   Selects: BACKLIGHT_CLASS_DEVICE [=y]                                                                                                                          &#9474;  
  &#9474;                                                  

I think that it's enabled, what do you think?

---

### Post by rodamu on 2011-05-15
*bump*

---

### Post by rodamu on 2011-05-15
Considering that the SONY_LAPTOP is Y by default (I still don't know how to edit this setting), after exiting the makeconfig, when I do "mount /boot" I get an error saying that /boot can't be found in /etc/fsab or /etc/mtab

any help in appreciated :)

---

