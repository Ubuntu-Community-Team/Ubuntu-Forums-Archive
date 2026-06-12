---
title: "Ubuntu 10.04 64bit showing only 2.7 GiB out of 4GiB"
date: 2010-11-05
forum: General Help
---

### Post by itsev on 2010-11-05
Good day to all,
I've just installed Ubuntu 10.04 64bit on my PC with 4GB of ram and the sysmon is showing only 2.7
Don't know why it's doing that, but don't like this. So far I red that I must enable PAE but since PAE is integrated into the kernel in this version, don't know how to proceed further. 

Here is what I've installed:

uname -a
Linux xxxxxxxx 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux

I'll be using this machine mainly for VMWare virtual machines and I was surprised how fast is it. Can't figure out why it's addressing only 2.7....

---

### Post by plucky on 2010-11-05
> **itsev said:**
> Good day to all,
I've just installed Ubuntu 10.04 64bit on my PC with 4GB of ram and the sysmon is showing only 2.7
Don't know why it's doing that, but don't like this. So far I red that I must enable PAE but since PAE is integrated into the kernel in this version, don't know how to proceed further. 

Here is what I've installed:

uname -a
Linux xxxxxxxx 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux

I'll be using this machine mainly for VMWare virtual machines and I was surprised how fast is it. Can't figure out why it's addressing only 2.7....

You are running the 64 bit version of Ubuntu so it should be able to see all your memory.You only need the PAE kernel if you are running the 32 bit system and wanted to see 4GB or more memory.

Can you see 4GB in the BIOS.

Run Memtest from the GRUB2 Menu and see how much memory that can see.


Then in Ubuntu, open a terminal and ```
free -m
```

Good Luck

---

### Post by CharlesA on 2010-11-05
Make sure that the BIOS sees all 4GB is the first step to troubleshooting memory problems.

---

### Post by itsev on 2010-11-06
hello there, thanks for your replies.
I definitely see all the memory in my BIOS, otherwise I would not ask for help.

I executed the command free -m and here's the output:

```
             total       used       free     shared    buffers     cached
Mem:          2756       1023       1732          0        162        418
-/+ buffers/cache:        443       2313
Swap:         5099          0       5099
```


I did the SWAP only 5GiB because I don't think that I need more with those 4GiB but that's why probably Ubuntu is recognizing only 2.7x2 = ~5 GiB

let me know if this is the case and I'll reinstall with 8 GiB of Swap

---

### Post by Bitrate on 2010-11-06
Check your BIOS settings and ensure than any memory remapping option is enabled.

---

### Post by CharlesA on 2010-11-06
What mobo do you have in that machine? I know the Atom boards have a limit of seeing 3.5GB of RAM, so if you dedicate 512MB to video, it'll only see 3GB of RAM, even on a 64-bit OS.

Chipset limitation I believe.

---

### Post by plucky on 2010-11-06
Are you sure you don't have 3Gb of memory as that is what is being seen by the operating system.

Post output of ```
sudo lshw -C memory
```

---

### Post by itsev on 2010-11-07
Hello guys, thanks for your replies. 

Please find the output below

```
  *-firmware              
       description: BIOS
       vendor: American Megatrends Inc.
       physical id: 0
       version: P1.00 (08/20/2008)
       size: 64KiB
       capacity: 448KiB
       capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
  *-cache:0
       description: L1 cache
       physical id: 5
       slot: L1-Cache
       size: 64KiB
       capacity: 64KiB
       capabilities: internal write-back data
  *-cache:1
       description: L2 cache
       physical id: 6
       slot: L2-Cache
       size: 2MiB
       capacity: 2MiB
       capabilities: internal write-back unified
  *-memory
       description: System Memory
       physical id: e
       slot: System board or motherboard
       size: 4GiB
     *-bank:0
          description: DIMM SDRAM Synchronous
          product: PartNum0
          vendor: Manufacturer0
          physical id: 0
          serial: SerNum0
          slot: DIMM0
          size: 2GiB
          width: 64 bits
     *-bank:1
          description: DIMM SDRAM Synchronous
          product: PartNum1
          vendor: Manufacturer1
          physical id: 1
          serial: SerNum1
          slot: DIMM1
          size: 2GiB
          width: 64 bits


```

---

### Post by UnrealMiniMe on 2010-11-10
I have a similar problem, only not nearly as severe, so I decided to bump this thread and hope something helpful comes from it. :)

---

### Post by blackmail on 2010-11-10
How nice the post shows that it sees both of the dimms and they both have 2 GB of RAM per piece, so then we should look elsewhere, could it be that indeed you have an onboard v-card and you gave it a bit too much memory, i also had the same "issue". In the bois i know you see the max installed RAM memory and in the OS you see the memory it can actually use, so that means it doesn't use that memory that is not shown there, how about you reset your bois configs to default? if that doesn't help i would suggest a reinstall of the ubuntu OS or just take the normal 64-bit kernel, from kernel.org and recompile that. There are instructions for that on the forum.

---

### Post by itsev on 2010-11-19
well, I'm sure that in BIOS I allocated only 128mb for the onboard VC

Installing from scratch did not fixed the problem... probably I'll go for the original 64bit kernel, but probably I'll need to reinstall my VMWare Workstation, cause there are modules compiled to be used with my current kernel... 

thanks anyway for your suggestions.

---

### Post by maticer on 2010-11-20
I was dealing with the same issue today and just hit the wall.. :icon_frown: ..my laptop Compaq nc6400 officially supports up to 4GB of DDR2, but it can actually work with just 3.3 GB as well explained here: [http://h30499.www3.hp.com/t5/Notebook-HP-Compaq-Armada-EVO/nc6400-4GB-memory-problem/td-p/839144/page/2](http://h30499.www3.hp.com/t5/Notebook-HP-Compaq-Armada-EVO/nc6400-4GB-memory-problem/td-p/839144/page/2)
[INDENT][I]The memory adressing limitation is in the chipset... 965m is  the only one with "full" 4 gb support... 945 only sees 3.37 and the  rest is mapped as a shared resource between the gpu and other  components...
[/I][/INDENT]But as searching further, it seems this could actually be fixed, but HP supprt is just to lazy for that I guess - to fix BIOS. That is based on this similar post: [http://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1290291672517+28353475&threadId=1159992](http://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1290291672517+28353475&threadId=1159992)

So I guess it must be something similar in your case... turn BIOS parameters upside down and try to find out memory remapping: PCI / APIC. Be sure also to check u got latest BIOS.

---

### Post by dcstar on 2010-11-20
> **maticer said:**
> I was dealing with the same issue today and just hit the wall.. :icon_frown: ..my laptop Compaq nc6400 officially supports up to 4GB of DDR2, but it can actually work with just 3.3 GB as well explained here: [http://h30499.www3.hp.com/t5/Notebook-HP-Compaq-Armada-EVO/nc6400-4GB-memory-problem/td-p/839144/page/2](http://h30499.www3.hp.com/t5/Notebook-HP-Compaq-Armada-EVO/nc6400-4GB-memory-problem/td-p/839144/page/2)
[INDENT][I]The memory adressing limitation is in the chipset... 965m is  the only one with "full" 4 gb support... 945 only sees 3.37 and the  rest is mapped as a shared resource between the gpu and other  components...
[/I][/INDENT]But as searching further, it seems this could actually be fixed, but HP supprt is just to lazy for that I guess - to fix BIOS. That is based on this similar post: [http://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1290291672517+28353475&threadId=1159992](http://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1290291672517+28353475&threadId=1159992)

So I guess it must be something similar in your case... turn BIOS parameters upside down and try to find out memory remapping: PCI / APIC. Be sure also to check u got latest BIOS.

People have to understand that a 4GB Address Limit is a **hardware** limit and if that limit exists then the addresses have to be **shared** between RAM and other system resources.

If a system is designed with a chipset that **only** goes up to 4GB maximum, then it will **not** be capable of mapping anything above that limit because the hardware will **not** have the necessary extra address bus.

Manufacturers will not waste money and resources designing hardware to work past the specs that they set for the particular unit that is designed. If you want hardware that will allow full 4GB or RAM to be used then get something designed to have more than 4GB of RAM, then the non-RAM address space will be able to be mapped above 4GB.

---

### Post by maticer on 2010-11-28
As far as I understood from other posts I read: some motherboards with this very same chipset do have available setting in BIOS to map the addresses, but some other, like mine don't have it - as I read setting is hardcoded and it can't be changed... :confused:

---

