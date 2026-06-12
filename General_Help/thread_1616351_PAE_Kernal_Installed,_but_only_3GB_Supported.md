---
title: "PAE Kernal Installed, but only 3GB Supported?"
date: 2010-11-08
forum: General Help
---

### Post by trilobyte- on 2010-11-08
Hi there.

I was wondering how to enable Ubuntu to support my 4GB of RAM I have. At the moment on the system page, it says I only have 3GB. But when I check my uname -a results it says:

```

Linux Unison 2.6.35-22-generic-pae #35-Ubuntu SMP Sat Oct 16 22:16:51 UTC 2010 i686 GNU/Linux

```So I'm fairly sure I have the PAE kernel, correct? If anyone could help me with this that'd be great.

Thanks. :)

---

### Post by P4man on 2010-11-08
Even with PAE, its still a 32 bit kernel, and as a result device mapping happens in the first 32 bit, ie, first 4GB. Depending on your hardware, that makes you lose anywhere between 0.5 and 1GB. 

It cant be avoided except by using a 64 bit kernel (assuming you have a 64 bit capable cpu).

---

### Post by trilobyte- on 2010-11-08
I have a 64bit Capable CPU, but I recently moved off of 64bit because I noticed there was a lot of things that didn't work properly. I didn't check then, but I'm still almost certain that there wasn't 4GB in use there either.

So there is no way to enable the full 4GB?

---

### Post by Verbeck on 2010-11-08
do you see all 4gb in bios?

---

### Post by Grenage on 2010-11-08
> **trilobyte- said:**
> I have a 64bit Capable CPU, but I recently moved off of 64bit because I noticed there was a lot of things that didn't work properly. I didn't check then, but I'm still almost certain that there wasn't 4GB in use there either.

So there is no way to enable the full 4GB?

Shared Video memory can and does poach system RAM.

---

### Post by 3Miro on 2010-11-08
With the 32-bit PAE kernel you should see about 3.8, 3.9GB of RAM. If not, check with your BIOS to make sure the motherboard supports 64-bit as well as any mapping/remapping option that may interfere with it.

---

### Post by P4man on 2010-11-08
> **3Miro said:**
> With the 32-bit PAE kernel you should see about 3.8, 3.9GB of RAM. 

As far as I know, with or without PAE, devices are still mapped in the 32 bit address space, so for instance a videocard with 512Mb or 1 GB will take up that much (virtual) address space. The default for  linux is 3GB address space for each process, 1GB for devices (on windows it used to be 2GB for either, unless you used the /3GB switch).

More info here:
[http://blogs.msdn.com/b/hiltonl/archive/2007/04/13/the-3gb-not-4gb-ram-problem.aspx](http://blogs.msdn.com/b/hiltonl/archive/2007/04/13/the-3gb-not-4gb-ram-problem.aspx)

The above is about windows, but the issue is exactly the same with linux. You cant use all the ram between 0 and 4GB with a 32 bit OS (though you can use beyond 4GB with PAE). And even with a 64 bit os and cpu, you might still not be able to use it, depending on your motherboard.

---

### Post by trilobyte- on 2010-11-08
> **Verbeck said:**
> do you see all 4gb in bios?

Yes, as well as in Windows 7 when it told me I had 4GB and only 3GB usable.

---

### Post by 3Miro on 2010-11-08
> **P4man said:**
> As far as I know, with or without PAE, devices are still mapped in the 32 bit address space, so for instance a videocard with 512Mb or 1 GB will take up that much (virtual) address space. The default for  linux is 3GB address space for each process, 1GB for devices (on windows it used to be 2GB for either, unless you used the /3GB switch).


This is true for generic 32-bit, the pae kernel has a hack that will let you see all of 32-bit. I am not sure exactly how it works, but I do have it on my mom's computer. It sees 3.9 GB of RAM with 512MB of Video RAM.

@trilobyte: the BIOS will detect 4GB of RAM, however, the video RAM has to be mapped to the lower end of the numbers. Newer BIOS would do that by default, older ones had to be either set manually or sometimes the BIOS itself had to be flushed to make it work. I am not very familiar with BIOS options, however, if you have Athlon 64 or Core 2 Duo CPU you can check this by booting from a Ubuntu 64-bit LiveCD. 

What is your motherboard?

---

### Post by trilobyte- on 2010-11-10
Hi there, sorry for the late reply, I've been busy with school work lately.

Here are my Motherboard specs:

```

Motherboard 
    CPU Type: DualCore Intel Pentrium E2180, 2000 MHz (10x200) 
    Motherboard Name: Asus P5N-MX  (2 PCI, 1 PCI-E x1, 1 PCI-E x16, 2 DDR2 DIMM,

```

---

