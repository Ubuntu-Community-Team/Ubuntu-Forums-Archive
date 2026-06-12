---
title: "Wrong RAM info"
date: 2010-06-19
forum: General Help
---

### Post by GeorgeOfTheBush on 2010-06-19
Ubuntu 10.04 System Monitor shows that my system has **2.9 GB** RAM as against **4 GB**. 

Windows Vista installed on my system shows this information correctly.

How should this be corrected on Ubuntu?

---

### Post by dino99 on 2010-06-19
its because you use i386 kernel(s), goto synaptic and install the "generic-pae" kernel instead, then remove the "generic" one(s)

all your ram will be seen and used with the generic-pae kernel

---

### Post by GeorgeOfTheBush on 2010-06-19
Thanks a lot dino99 for your super-quick response!

I am an Ubuntu  newbie and hence need some more info.

Is this the correct command to download and install the "**PAE**" kernel? 

```

**[COLOR=Blue]sudo apt-get install linux-generic-pae linux-headers-generic-pae[/COLOR]**

```Also, will this ensure that from the next time onwards whenever Update  Manager detects a kernel update, it would _automatically_ pick the [COLOR=Red]**PAE kernel**[/COLOR] instead of the generic one?

Thanks again!

---

### Post by warfacegod on 2010-06-19
> **GeorgeOfTheBush said:**
> Ubuntu 10.04 System Monitor shows that my system has **2.9 GB** RAM as against **4 GB**. 

Windows Vista installed on my system shows this information correctly.

How should this be corrected on Ubuntu?

FYI: Just because Vista was able to display the correct amount of RAM doesn't mean it was able to address it. If it was 32 bit, it was only using the same 2.9 GB. Folks were complaining to about Windows nit seeing all of there RAM so MS, instead of making the 32 bit OS's able to *use* all the RAM, opted to make the 32's able to *see* all the RAM.

Your two options are to go with the pae kernel as dino99 suggests or go with a 64 bit OS if your computer supports it.

To find out, go to: Applications> Accessories> Terminal:

```
sudo lshw
```

Your password will remain blank when you type, just hit enter. Now scroll back up until you see something similar to this:

```
   *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: NWD
          size: 2800MHz
          capacity: 3200MHz
***          width: 32 bits***
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0

```

I've emphasized the part you are looking for. If your says width: 64 bits then I recommend installing with 10.04 64 bits. If it says 32 bit then your only option is the pae kernel.

---

### Post by GeorgeOfTheBush on 2010-06-19
Thanks WARFACEGOD for your detailed explanation.

My system does support 64 bit OS as can be seen below.

```

*-cpu:0
          description: CPU
          product: Pentium(R) Dual-Core CPU       T4200  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: U2E1
          size: 1200MHz
          capacity: 4096MHz
          width: [SIZE=4][COLOR=Blue]**64 bits**[/COLOR][/SIZE]
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm cpufreq
          configuration: id=1

```

I was told that you [COLOR=Red]don't[/COLOR] see a significant improvement in performance with a [COLOR=Blue]64 bit[/COLOR] OS, hence I settled for [COLOR=Blue]Ubuntu 32 bit Lucid Lynx[/COLOR].

What is your take on this opinion? Would you [COLOR=Blue]recommend[/COLOR] going for the **[COLOR=Blue]64bit OS[/COLOR]** **or** [COLOR=Blue]**the PAE kernel**[/COLOR]?

---

### Post by warfacegod on 2010-06-19
It depends on what you are using your computer for. Video encoding/editing will probably see an obvious speed boost with 64 bit. Boot up will probably be faster with 64. Other things such as web browsing will likely be no different or not much.

I recently found my mother a refurbished HP laptop with very similar specs to my own laptop. The *main* difference being her processor was AMD TurionX2 @ 2.4 GHz 64 bit and mine is Intel Pentium4 Hyper Thread @ 2.8 GHz. Hers got Lucid 64 and mine has Karmic 32. I noticed between slight and moderate differences in performance in the two, using identical apps. Starting Open Office and running Gnome Mplayer (video) and Flash videos online were the three big winners on hers. Mine was able to install packages *slightly* faster.

As a whole, if I had my druthers, I'd go with 64. It's a somewhat peppier. > I was told that you don't see a significant improvement in performance with a 64 bit  OS
Allot of this depends on the machine in use. Some will see zero to marginal improvements and some will see astonishing speed boosts.

Here is what I suggest you do. Go with the pae kernel in your current install and create a new partition to install 64 bit into. Use one exclusively for several days and then the other. That, I think, will give you the best basis for judging which is best for you.

---

### Post by jocko on 2010-06-19
> **GeorgeOfTheBush said:**
> Thanks WARFACEGOD for your detailed explanation.

My system does support 64 bit OS as can be seen below.

```

*-cpu:0
          description: CPU
          product: Pentium(R) Dual-Core CPU       T4200  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: U2E1
          size: 1200MHz
          capacity: 4096MHz
          width: [SIZE=4][COLOR=Blue]**64 bits**[/COLOR][/SIZE]
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm cpufreq
          configuration: id=1

```I was told that you [COLOR=Red]don't[/COLOR] see a significant improvement in performance with a [COLOR=Blue]64 bit[/COLOR] OS, hence I settled for [COLOR=Blue]Ubuntu 32 bit Lucid Lynx[/COLOR].

What is your take on this opinion? Would you [COLOR=Blue]recommend[/COLOR] going for the **[COLOR=Blue]64bit OS[/COLOR]** **or** [COLOR=Blue]**the PAE kernel**[/COLOR]?

[Phoronix did a test]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1") on that a while back. As you can see in the test, 64 bit outperformed 32 bit (with or without PAE) in every test except OpenGL, where the results were a tie. Some of the differences may be smaller than what you would be able to notice, but others are definitively noticeable. It depends on what you do with your computer.

---

### Post by warfacegod on 2010-06-19
> Phoronix did a test on that a while back. As you can see in the test, 64 bit outperformed 32 bit (with or without PAE) in every test except OpenGL, where the results were a tie. Some of the differences may be smaller than what you would be able to notice, but others are definitively noticeable. It depends on what you do with your computer. 

Grant you, all I used was the stopwatch function on my cellphone and my "feel" for computers.

---

### Post by GeorgeOfTheBush on 2010-06-19
Thanks WARFACEGOD & JOCKO for your help!

If I were to run [COLOR=Blue]**Compiz + Beryl**[/COLOR] for stunning graphics effects, would the [COLOR=Blue]**64bit OS**[/COLOR] still be the better choice?

---

### Post by warfacegod on 2010-06-19
> **GeorgeOfTheBush said:**
> Thanks WARFACEGOD & JOCKO for your help!

If I were to run [COLOR=Blue]**Compiz + Beryl**[/COLOR] for stunning graphics effects, would the [COLOR=Blue]**64bit OS**[/COLOR] still be the better choice?

Probably. Compiz depends more on the type of video card you have and more specifically how good the driver is for it.

If you have nVidia, you're already in great shape.

An ATi card can be hit or miss but they're getting better.

Intel graphics? You're better off trying to use your fingers to pull out your own teeth and pluck the eyes from your head.

---

### Post by uOpt on 2010-06-19
To get 4 out of 4 GB you don't only need a 64 bit or PAE kernel. You also need working BIOS support to remap the memory from 3-4 GB to 4-5 GB. And some mainboard chipsets don't do that at all, even if the BIOS wanted to, such as the intel 945 POS chipset.

Please post a screenshot of where exactly Vista says it sees 4 GB, that will help.

---

### Post by GeorgeOfTheBush on 2010-06-19
Hi uOpt

  I have Vista 64-bit OS installed as can be seen in the snapshot attached.

---

### Post by impact on 2010-06-19
> **warfacegod said:**
> It depends on what you are using your computer for. Video encoding/editing will probably see an obvious speed boost with 64 bit. Boot up will probably be faster with 64. Other things such as web browsing will likely be no different or not much.

I recently found my mother a refurbished HP laptop with very similar specs to my own laptop. The *main* difference being her processor was AMD TurionX2 @ 2.4 GHz 64 bit and mine is Intel Pentium4 Hyper Thread @ 2.8 GHz. Hers got Lucid 64 and mine has Karmic 32. I noticed between slight and moderate differences in performance in the two, using identical apps. Starting Open Office and running Gnome Mplayer (video) and Flash videos online were the three big winners on hers. Mine was able to install packages *slightly* faster.

As a whole, if I had my druthers, I'd go with 64. It's a somewhat peppier. 
Allot of this depends on the machine in use. Some will see zero to marginal improvements and some will see astonishing speed boosts.

Here is what I suggest you do. Go with the pae kernel in your current install and create a new partition to install 64 bit into. Use one exclusively for several days and then the other. That, I think, will give you the best basis for judging which is best for you.

You can performs some ext4 tweaks to speed up your disk. Check this: [http://blog.smartlogicsolutions.com/2009/06/04/mount-options-to-improve-ext4-file-system-performance/](http://blog.smartlogicsolutions.com/2009/06/04/mount-options-to-improve-ext4-file-system-performance/)

edit: you might want to backup any important files before you start tweaking

---

### Post by warfacegod on 2010-06-19
As a base comparison between the pae kernel and a 64 bit OS, an non-tweaked system would probably be best. By all means tweak away after choosing which route to go. Looks like the link has some solid info.

---

