---
title: "PAE not working correctly, still only 3.3 GiB RAM"
date: 2010-09-28
forum: General Help
---

### Post by msundman on 2010-09-28
I cannot get PAE to work on lucid. I have 4 GiB of RAM installed, but System Monitor says "Memory: 3.3 GiB".
```
$ uname -a
Linux hal 2.6.32-25-generic-pae #44-Ubuntu SMP Fri Sep 17 21:57:48 UTC 2010 i686 GNU/Linux
$ lshw 2>/dev/null | grep 'CPU '
          product: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz
$ lshw 2>/dev/null|grep ' pae '
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow cpufreq
$ 
```

Any ideas?

---

### Post by apjone on 2010-09-29
Basically unless you install the 64bit version of an OS you can not make use of the full 4GB of RAM 

[http://www.zdnet.com/blog/hardware/clearing-up-the-3264-bit-memory-limit-confusion/3124](http://www.zdnet.com/blog/hardware/clearing-up-the-3264-bit-memory-limit-confusion/3124)
-and-
[http://www.dansdata.com/askdan00015.htm](http://www.dansdata.com/askdan00015.htm)

---

### Post by goodolandy on 2010-09-29
@msundman

Part of your ram might be defective.  I have 4 GB in mine on the same Kernel version as you and mine is showing the full 4.  Try running a memory diagnostic on boot-up to make sure you don't have defective ram.

---

### Post by msundman on 2010-09-29
> **apjone said:**
> Basically unless you install the 64bit version of an OS you can not make use of the full 4GB of RAM
With PAE one is supposed to be able to address up to 64 GiB of RAM. I'm using the PAE kernel.

---

### Post by msundman on 2010-09-29
> **goodolandy said:**
> Part of your ram might be defective.  I have 4 GB in mine on the same Kernel version as you and mine is showing the full 4.  Try running a memory diagnostic on boot-up to make sure you don't have defective ram.
I've done that. I've checked both 2 GiB SO-DIMM modules separately, and I've checked the 3.X (where X was something like 5 or 6) GiB together which is how much memory the BIOS reports there to be. I've checked the RAM both with my BIOS's built-in checker and with the memtest86+ on the 64bit ubuntu install iso.

---

### Post by goodolandy on 2010-09-29
If your BIOS doesn't see the full 4 then I would think that the operating system would also not see the full 4.  If the MB is suppose to see 4GB then maybe see if there is any BIOS firmware update for your board that addresses this issue.

---

### Post by lfforman on 2010-09-29
are u using a inboard graphic card or a separate graphic card? if the first option is true the memory is not showing is being used by the graphic card. i have PAE installed and i see all 4 gbytes of memory, but i have a separate nvidia card.

---

### Post by bartomania on 2010-09-29
Hi

I'm having the same problem here. I just bought 2x2GB banks, added them to my MSI MS-7235 motherboard (which added to the other 2x512MB I had, should sum 5 GB) but my system is only recognizing 3.2 GB.

Some info about my system:

Ubuntu 10.4
uname -a: Linux tarantino 2.6.32-25-generic-pae #44-Ubuntu SMP Fri Sep 17 21:57:48 UTC 2010 i686 GNU/Linux

CPU: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
Motherboard: MSI MS-7235
Memory: 2x2GB OCZ PC6400 + 2x512GM OCZ PC6400
Graphic card: GeForce 6500

I've noticed that when it boots (in the initial memory count) it only recognizes the 3.2GB. I thought it might be a problem with the mobo, but I checked and it's supposed to support up to 8 GB.

Any ideas?

---

### Post by eexpress on 2010-09-29
my machine is  I3+GT240+2x2G

10.04 new install, only 2G works.

at this page: [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE) , i saw 10.04 is default enable pae...

yesterday, i install linux-generic-pae linux-headers-generic-pae
and reinstall nvidia-common and nvidia-settings.

i saw nvidia only rebuild on linux-generic kernel, but not on pae kernel.

when start pae from grub, all fail.

maybe i need check my bios setting now.
```
BIOS-chipset--north bridge configuration-memory remap reature => enabled
```

or anyone can suggest more.

---

### Post by soldier1st on 2010-09-30
32bit is limited to 3-4GB depending on your hardware/etc... but if you say have 6GB and your mobo supports up to 8GB then the only way to access that 6GB is to install 64bit linux.

---

### Post by PRC09 on 2010-09-30
I am running an ASUS M2N68-AM PLUS motherboard and it is listed as being capable of 8GB ram.I only have 4GB installed and am running both 64bit and 32 bit PAE and they both recognise the ram as 3.6GB with an onboard video of 256 shared ram.The standard 32 bit install only recognized 2.6 so the PAE kernel does work......

---

### Post by yetiman64 on 2010-09-30
> **soldier1st said:**
> 32bit is limited to 3-4GB depending on your hardware/etc... but if you say have 6GB and your mobo supports up to 8GB **then the only way to access that 6GB is to install 64bit linux**.

This is wrong, the idea of a pae (physical address extension) kernel, is to allow a 32 bit OS to address more than the 4G RAM limit normally associated to 32 bit systems.

My system here is a 64 bit quad core with 8 GB RAM and has multiple installations of Ubuntu including 32 bit installs. All the 32 bit installs (with the exception of Jaunty - no pae kernel that I know of available) have both the normal kernel and its pae equivalent installed.

An example, my 32 bit Lucid install (Note: Lucid installs the pae kernel by default on this hardware and I had to specifically install the generic kernel) gives ~ 2.8 GB of RAM when the generic kernel is booted and ~ 7.7 GB RAM when the pae kernel gets booted.

Not sure why your pae kernel is not seeing all your RAM (It should see significanty more), but it warrants further checking (possibly run a memtest check on the modules and rule out hardware faults first).

> I am running an ASUS M2N68-AM PLUS motherboard and it is listed as being  capable of 8GB ram.I only have 4GB installed and am running both 64bit  and 32 bit PAE and they both recognise the ram as 3.6GB with an onboard  video of 256 shared ram.The standard 32 bit install only recognized 2.6  so the PAE kernel does work......     +1 agree pae kernels **do** work.

---

### Post by msundman on 2010-09-30
> **goodolandy said:**
> If your BIOS doesn't see the full 4 then I would think that the operating system would also not see the full 4.  If the MB is suppose to see 4GB then maybe see if there is any BIOS firmware update for your board that addresses this issue.
Actually the BIOS sees the full 4 GiB, and the BIOS has a memory tester, in which all of the 4096 MiB RAM is shown as passing all the tests. However, memtest86+ sees only "3447 M" (or "3448 M", depending on the screen in memtest86+) using the BIOS memsize (if I use the "probe" memsize it locks up, which it does with all my current computers).

> **lfforman said:**
> are u using a inboard graphic card or a separate graphic card? if the first option is true the memory is not showing is being used by the graphic card. i have PAE installed and i see all 4 gbytes of memory, but i have a separate nvidia card.
I'm using an inboard graphics adapter ("Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"). However, when I was using 2 GiB of RAM I could see almost all of it (much, much more than, say, 1.3 GiB) in top or system monitor, but now when I have 4 GiB of RAM (and everything else is the same) I see only "3476544k" in top and "3.3 GiB" in system monitor.

---

### Post by msundman on 2010-09-30
> **yetiman64 said:**
> Not sure why your pae kernel is not seeing all your RAM (It should see significanty more), but it warrants further checking (possibly run a memtest check on the modules and rule out hardware faults first).
Done that. In my BIOS's internal memory checker the whole 4096 MiB pass all tests. In memtest86+ I've only been able to test "3447 M", which passes. I've also removed one of the SO-DIMMs, then used memtest86+ to check the other (and all of the ~2 GiB of it passes), then inserted the other SO-DIMM into the empty slot and removed the newly checked SO-DIMM from its slot and re-run memtest86+ (and all of the ~2 GiB of it passes), then re-inserted the first SO-DIMM and re-run memtest86+ at which point it sees only "3447 M" (which passes the tests, though).

---

### Post by yetiman64 on 2010-09-30
> **msundman said:**
> Done that. In my BIOS's internal memory checker the whole 4096 MiB pass all tests. In memtest86+ I've only been able to test "3447 M", which passes. I've also removed one of the SO-DIMMs, then used memtest86+ to check the other (and all of the ~2 GiB of it passes), then inserted the other SO-DIMM into the empty slot and removed the newly checked SO-DIMM from its slot and re-run memtest86+ (and all of the ~2 GiB of it passes), then re-inserted the first SO-DIMM and re-run memtest86+ at which point it sees only "3447 M" (which passes the tests, though).

That has me a bit :confused:, got the method you used and that, but the memtest only seeing ~3.45 GB has me puzzled. From your first post your hardware seems to support what you are trying and something seems amiss with the memtest bit.
>  capabilities:...pae....x86-64... <editted for brevity>


---

### Post by msundman on 2010-09-30
Is there perhaps some way to:
[LIST=1][*]see which memory ranges are available for RAM use (i.e., excluding ranges used for graphics adapters and other somesuch), and[*]tell the kernel which memory range(s) to use for RAM?[/LIST]
(I have a faint memory that I needed to add some option in grub when I put 4 GiB of RAM into one of my desktop computers running an amd64 kernel.)

---

### Post by migs73 on 2010-09-30
Did you also check that PAE or the NX bit are enabled in your BIOS??

BTW I have onboard graphics with 4GB RAM and PAE. OS sees 3.8GiB. Also note that although your OS may be able to address your 4GB RAM, the 32bit software you run on it wan't address more than about 3GB at a time.

---

### Post by JedMeister on 2010-09-30
double post - sorry!

---

### Post by JedMeister on 2010-09-30
I don't know enough and haven't tested enough of this stuff to be sure but I have read a little about it (although mostly online, so perhaps some of my info is misguided).  

I have read about 'missing' memory due to a "memory hole". This is apparently when hardware is allocated significant amounts of the address space between 3 & 4GB which creates a RAM 'shadow'. In other words the RAM is still there but not available because the addresses are being used elsewhere by hardware eg GPU, etc. AFAIK 64 bit OS (somehow) get around that by remapping those addresses, whereas (for whatever reason) 32 bit ones don't (can't?) even with PAE - unless it is supported by the BIOS (I have read of BIOS options to remap the "memory hole"). If what I have read is correct then it would make sense that BIOS sees all the RAM but its not available to a 32 bit OS. If this theory is correct, if you added more RAM, bought it up to say 6GB then you would end up with around 5.3GB usable RAM (assuming only 3.3 -> 4GB is 'shadowed'). Also if you got a GPU with more onboard RAM then the RAM recognised by your OS would go down (due to 'shadow'). 

If I'm right, then the only way around it may be checking for BIOS options around remapping addresses, changing 'shadow' behaviour or other such things (some suggested above). Also check for an updated BIOS (as also suggested). Or installing a 64 bit (worth at least trying a live CD to see whether that works).

Also to chip in my 2c about the misconceptions that PAE doesn't work to allow use of greater than ~3GB RAM. I believe that this error has crept in because of MS. Because of Win design, while PAE remedies the issue of memory above ~3GB it also raises some serious compatibility problems. For example the way device drivers are designed to work in Win means that if you have a 32 bit PAE enabled OS you need 64 bit aware drivers (but they still need to operate in a 32 bit environment). As you would imagine that caused issues (and no doubt many complaints) so MS disabled the full effectiveness of the /PAE boot switch (AFAIK that was around XP SP1). Hence for Windows - definitely XP but also Vista I think. AFAIK its enabled by default (and works correctly) in Win7 - please correct me if I'm wrong.

---

### Post by migs73 on 2010-09-30
> **JedMeister said:**
> I don't know enough and haven't tested enough of this stuff to be sure but I have read a little about it (although mostly online, so perhaps some of my info is misguided).  

I have read about 'missing' memory due to a "memory hole". This is apparently when hardware is allocated significant amounts of the address space between 3 & 4GB which creates a RAM 'shadow'. In other words the RAM is still there but not available because the addresses are being used elsewhere by hardware eg GPU, etc. AFAIK 64 bit OS (somehow) get around that by remapping those addresses, whereas (for whatever reason) 32 bit ones don't (can't?) even with PAE - unless it is supported by the BIOS (I have read of BIOS options to remap the "memory hole"). If what I have read is correct then it would make sense that BIOS sees all the RAM but its not available to a 32 bit OS. If this theory is correct, if you added more RAM, bought it up to say 6GB then you would end up with around 5.3GB usable RAM (assuming only 3.3 -> 4GB is 'shadowed'). Also if you got a GPU with more onboard RAM then the RAM recognised by your OS would go down (due to 'shadow'). 

If I'm right, then the only way around it may be checking for BIOS options around remapping addresses, changing 'shadow' behaviour or other such things (some suggested above). Also check for an updated BIOS (as also suggested). Or installing a 64 bit (worth at least trying a live CD to see whether that works).

Also to chip in my 2c about the misconceptions that PAE doesn't work to allow use of greater than ~3GB RAM. I believe that this error has crept in because of MS. Because of Win design, while PAE remedies the issue of memory above ~3GB it also raises some serious compatibility problems. For example the way device drivers are designed to work in Win means that if you have a 32 bit PAE enabled OS you need 64 bit aware drivers (but they still need to operate in a 32 bit environment). As you would imagine that caused issues (and no doubt many complaints) so MS disabled the full effectiveness of the /PAE boot switch (AFAIK that was around XP SP1). Hence for Windows - definitely XP but also Vista I think. AFAIK its enabled by default (and works correctly) in Win7 - please correct me if I'm wrong.

I had heard of this too, just thought they had better check that PAE was enabled in the BIOS first. Then if still a problem find out if you system can run 64bit
```
cat /proc/cpuinfo | grep flags
``` 
and if the list has 'lm' in it (Long Mode) then your processor is 64bit'able'. Mine is, just haven't tried it yet. Maybe I'll go for Maverick 64 RC? :P

---

### Post by soldier1st on 2010-10-02
> **yetiman64 said:**
> This is wrong, the idea of a pae (physical address extension) kernel, is to allow a 32 bit OS to address more than the 4G RAM limit normally associated to 32 bit systems.

My system here is a 64 bit quad core with 8 GB RAM and has multiple installations of Ubuntu including 32 bit installs. All the 32 bit installs (with the exception of Jaunty - no pae kernel that I know of available) have both the normal kernel and its pae equivalent installed.

An example, my 32 bit Lucid install (Note: Lucid installs the pae kernel by default on this hardware and I had to specifically install the generic kernel) gives ~ 2.8 GB of RAM when the generic kernel is booted and ~ 7.7 GB RAM when the pae kernel gets booted.

Not sure why your pae kernel is not seeing all your RAM (It should see significanty more), but it warrants further checking (possibly run a memtest check on the modules and rule out hardware faults first).

+1 agree pae kernels **do** work.
all the memory works but here is the strange thing. before i had 4GB(max) then the bios would not show more than 2.5GB availible out of say 3GB even after setting hardware/software remapping to on from disabled but since i put 1GB in each (4GB) and i enable hardware/software remapping then the bios will show all 4GB as availible but linux won't boot(i will get the info later as to why it won't)it will if i return the setting back to the original setting, i know your not supposed to get all the memory availible for use after a certain point due to hardware addressing(it has to get it from somewhere)i'm only telling you from what i was told(source probably does not know all the info)also i have a 1GB video card so that will cut down on how much is availible.

---

### Post by yetiman64 on 2010-10-02
> **soldier1st said:**
> all the memory works but here is the strange thing. before i had 4GB(max) then the bios would not show more than 2.5GB availible out of say 3GB even after setting hardware/software remapping to on from disabled but since i put 1GB in each (4GB) and i enable hardware/software remapping then the bios will show all 4GB as availible but linux won't boot(i will get the info later as to why it won't)it will if i return the setting back to the original setting, i know your not supposed to get all the memory availible for use after a certain point due to hardware addressing(it has to get it from somewhere)i'm only telling you from what i was told(source probably does not know all the info)also i have a 1GB video card so that will cut down on how much is availible.

Sounds as though might be a hardware or BIOS (I'm thinking; update needed perhaps?) but not a pae issue as such.

Re your info, -- may have meant your *_hardware_* has to be 64 bit capable but 64 bit hardware can execute *_either_* 64 or 32 bit code. The pae kernel specifically allows the OS to access more than 4GB of RAM and in my case gives me 7.7 GB of 8GB RAM on a 32 bit system install.

There seems to be some issue  with the OP's case (and sounds like your's as well) that as much RAM seems to be missing and could be accounted for by BIOS setup or other hardware issues.

---

### Post by dcstar on 2010-10-03
> **msundman said:**
> 
.........
I'm using an inboard graphics adapter ("Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"). However, when I was using 2 GiB of RAM I could see almost all of it (much, much more than, say, 1.3 GiB) in top or system monitor, but now when I have 4 GiB of RAM (and everything else is the same) I see only "3476544k" in top and "3.3 GiB" in system monitor.

[LIST=1]
[*]Gib <> GB, they are different measurement units.
[*]For 32-bit compatibility all addresses of internal devices must be mapped below 4GB.
[*]PAE means a single process can still only access 4GB of address space maximum, using a PAE kernel means that separate processes can use separate parts of your RAM in 4GB chunks.
[*]PAE kernels come with efficiency downsides due to mapping these 4GB chunks.
[/LIST]

---

### Post by eexpress on 2010-10-03
solved. after install linux.*server. before this, i only install pae packages.
3.8G recongnized.

---

### Post by soldier1st on 2010-10-14
> **yetiman64 said:**
> Sounds as though might be a hardware or BIOS (I'm thinking; update needed perhaps?) but not a pae issue as such.

Re your info, -- may have meant your *_hardware_* has to be 64 bit capable but 64 bit hardware can execute *_either_* 64 or 32 bit code. The pae kernel specifically allows the OS to access more than 4GB of RAM and in my case gives me 7.7 GB of 8GB RAM on a 32 bit system install.

There seems to be some issue  with the OP's case (and sounds like your's as well) that as much RAM seems to be missing and could be accounted for by BIOS setup or other hardware issues.

i discovered the issue though i may not have all 4GB but i did gain 500MB of usable memory. one of those options(hardware option) i said of only supported a certain revision of the mobo(which mine does not as it wants E revision but mine is a revison i believe). enabling the software option allows more memory to be usable and Ubuntu boots properly.

---

### Post by maticer on 2010-11-20
Since I was dealing with this issue most of the evening today to figure out where I've lost 0.7 GiB of RAM and this was one of my first post that I found on Google and gave me a few ideas where to search, I tought I should post link to my conclusion: [**Ubuntu 10.04 64bit not showing 4GiB**]("http://ubuntuforums.org/showthread.php?p=10141957#post10141957") (my laptop supports 64bit OSes so I was trying that out, but had no luck either with that)

Unfortunately looks like there is **no solution for me - memory address remap is not available in BIOS of my laptop** and I'll have to live with just 3.3 GiB RAM. :(

---

### Post by frogotronic on 2011-01-13
> **maticer said:**
> Since I was dealing with this issue most of the evening today to figure out where I've lost 0.7 GiB of RAM and this was one of my first post that I found on Google and gave me a few ideas where to search, I tought I should post link to my conclusion: [**Ubuntu 10.04 64bit not showing 4GiB**]("http://ubuntuforums.org/showthread.php?p=10141957#post10141957") (my laptop supports 64bit OSes so I was trying that out, but had no luck either with that)

Unfortunately looks like there is **no solution for me - memory address remap is not available in BIOS of my laptop** and I'll have to live with just 3.3 GiB RAM. :(

Everyone here should note that to successfully use PAE kernels, you must install ALL the proper packages.

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

Ubuntu 9.10 and later

The relevant packages are:

```
 linux-image-generic-pae  linux-image-<version number>-generic-pae linux-headers-generic-pae linux-headers-<version number>-generic-pae
```

Regards,
CH

---

