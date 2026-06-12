---
title: "Only 2.9 of 4 GB (Install ram) available"
date: 2011-01-20
forum: General Help
---

### Post by dlcomm on 2011-01-20
This question was asked years ago, however I have a Toshiba Satellite L675 with 4 GB of ram installed.
For some reason I can only see 2.9 GB available with 2.5 GB free.   

The previous forum discussed changing BIOS settings to allow for a software memory hole and a few other tweaks, however the BIOS on this pile of junk doesn't let me make any changes to the RAM, Power or pretty much any other settings.

Does anyone know of any other way to get Ubuntu to see the full amout of installed RAM?

* I tried running Centos 5.5 and it has too many issues with the video card and Fedora sees the full amount of RAM but requires to many modifications to get some of the hardware / software to work.   So far Ubuntu has been the best solution, however I want to run VMWare from time to time and this will limit my abilities.

---

### Post by uRock on 2011-01-20
Hello and welcome to the forums!

Can you open a terminal and enter the following command, then post the output here?
```
free -m
```

To create code tags, click the # button int the post tool bar, then paste the output in between the tags.

---

### Post by sisco311 on 2011-01-20
Hi and welcome to the forums!

You have to use the PAE kernel. Ubuntu 10.04 or newer should automatically install it for you. If you are using an earlier version you have to install it manually.

See: [uhelp]community/EnablingPAE[/uhelp]

---

### Post by akand074 on 2011-01-20
That, or install 64 bit Ubuntu. I'm sure your system supports it, but better to make sure.

---

### Post by dlcomm on 2011-01-20
Thanks for all the input.... BTW - I am new to ubuntu but have been running linux since 1995 and have run pretty much ever release from RedHat to Madnrake, Fedora, Centos and Debian (now including Ubuntu).

So far, I am most impressed with Ubuntu even though I was never much of a fan of Debian.


Here is some of the info on my machine....

```
free -m
             total       used       free     shared    buffers     cached
Mem:          2947        896       2050          0         75        470
-/+ buffers/cache:        350       2596
Swap:        11998          0      11998

uname -r
2.6.35-24-generic

I also generated this report using hardinfo....


[SIZE=1]Computer[/SIZE] [SIZE=1]Processor[/SIZE][SIZE=1]4x Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz[/SIZE] 
[SIZE=1]Memory[/SIZE][SIZE=1]3017MB (471MB used)[/SIZE]
[SIZE=1]Operating System[/SIZE][SIZE=1]Ubuntu 10.10[/SIZE] 
[SIZE=1]User Name [/SIZE][SIZE=1]dlcomm (dlcomm)[/SIZE] 
[SIZE=1]Date/Time[/SIZE][SIZE=1]Thu 20 Jan 2011 05:10:44 PM PST[/SIZE] 
[SIZE=1]Display[/SIZE] [SIZE=1]Resolution[/SIZE][SIZE=1]1600x900 pixels[/SIZE] 
[SIZE=1]OpenGL Renderer [/SIZE][SIZE=1]Unknown[/SIZE] [SIZE=1]X11 
Vendor [/SIZE][SIZE=1]The X.Org Foundation[/SIZE] 
[SIZE=1]Multimedia[/SIZE] [SIZE=1]Audio Adapter [/SIZE][SIZE=1]HDA-Intel - HDA Intel[/SIZE] [SIZE=1]Input 
Devices[/SIZE] [SIZE=1] Lid Switch[/SIZE][SIZE=1]
[/SIZE] [SIZE=1] Power Button[/SIZE][SIZE=1]
  [/SIZE][SIZE=1]
[/SIZE] [SIZE=1] AT Translated Set 2 keyboard[/SIZE][SIZE=1]
[/SIZE] [SIZE=1] Video Bus[/SIZE][SIZE=1]
[/SIZE] [SIZE=1] CNF9055[/SIZE][SIZE=1]
[/SIZE] [SIZE=1] SynPS/2 Synaptics TouchPad[/SIZE][SIZE=1]
[/SIZE] [SIZE=1]Printers[/SIZE] [SIZE=1]No printers found[/SIZE]
[SIZE=1]SCSI Disks[/SIZE] [SIZE=1]ATA TOSHIBA MK6465GS[/SIZE]
[SIZE=1]TSSTcorp CDDVDW TS-L633C[/SIZE]
[SIZE=1]Generic- Multi-Card[/SIZE]

[SIZE=1]Operating System[/SIZE] 
[SIZE=1]Version[/SIZE] 
[SIZE=1]Kernel [/SIZE][SIZE=1]Linux 2.6.35-24-generic (i686)[/SIZE] 
[SIZE=1]Compiled[/SIZE][SIZE=1]#42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010[/SIZE] 
[SIZE=1]C Library[/SIZE][SIZE=1] GNU C Library version 2.12.1 (stable)[/SIZE] 
[SIZE=1]Default C Compiler [/SIZE][SIZE=1]GNU C Compiler version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) [/SIZE] 
[SIZE=1]Distribution[/SIZE][SIZE=1]Ubuntu 10.10[/SIZE] 
[SIZE=1]Current Session[/SIZE] 
[SIZE=1]Computer Name[/SIZE][SIZE=1]Satellite-L675[/SIZE] 
[SIZE=1]User Name[/SIZE][SIZE=1] dlcomm (dlcomm)[/SIZE] 
[SIZE=1]Desktop Environment[/SIZE][SIZE=1] GNOME 2.32.0[/SIZE] 
[SIZE=1]Misc[/SIZE] 
[SIZE=1]Uptime[/SIZE][SIZE=1]1 hour, 25 minutes[/SIZE] 
[SIZE=1]Load Average[/SIZE][SIZE=1]2.14, 2.16, 1.65[/SIZE] 
[SIZE=1]Kernel Modules[/SIZE] [SIZE=1]Loaded Modules[/SIZE] [SIZE=1]aes_i586[/SIZE][SIZE=1] Rijndael (AES) 
Cipher Algorithm, asm optimized[/SIZE] [SIZE=1]aes_generic[/SIZE][SIZE=1]Rijndael (AES) Cipher Algorithm[/SIZE] [SIZE=1]
ip6table_filter[/SIZE][SIZE=1]ip6tables filter table[/SIZE] [SIZE=1]ip6_tables[/SIZE][SIZE=1]IPv6 packet filter[/SIZE] [SIZE=1]binfmt_misc[/SIZE][SIZE=1]
[/SIZE] [SIZE=1]ipt_MASQUERADE[/SIZE][SIZE=1]Xtables: automatic-address SNAT[/SIZE] [SIZE=1]iptable_nat[/SIZE][SIZE=1]
[/SIZE] [SIZE=1]nf_nat[/SIZE][SIZE=1]
[/SIZE] [SIZE=1]nf_conntrack_ipv4[/SIZE][SIZE=1]
[/SIZE] [SIZE=1]nf_defrag_ipv4[/SIZE][SIZE=1]
[/SIZE] [SIZE=1]xt_state[/SIZE][SIZE=1]ip[6]_tables connection tracking state match module[/SIZE] [SIZE=1]nf_conntrack[/SIZE][SIZE=1]
```
[/SIZE] [SIZE=1]
I hope this helps narrow down this issue![/SIZE]

---

### Post by amauk on 2011-01-20
you're running the 32bit version

You can either run the PAE enabled kernel
(it's a hack to enable >4Gb RAM on 32bit)

or just run the 64bit version

---

### Post by uRock on 2011-01-20
I recommend installing 64bit. It'll be more snappy and it will be able to better utilize your RAM.

Cheers,
uRock

---

### Post by dlcomm on 2011-01-20
Thanks everyone..... since I am one who hates it when people don't  follow up on the posts...  I will try to not do that myself...

I installed the PAE kernel and it now sees the full amount of RAM!   I had a strange issue on the first boot where my glidepad was not working but a proper shutdown and restart of the machine cleared that issue.

I think I will just install the 64bit version in any case but thanks to all for the input and suggestions.

---

### Post by James78 on 2011-01-20
I have the same problem. 4GB of RAM, only 2.99GB being shown.. Using 64 bit.. Quite frustrating. :(

free -m for anyone interested
```
             total       used       free     shared    buffers     cached
Mem:          3008       2794        213          0        224       1654
-/+ buffers/cache:        916       2092
Swap:         4692         13       4679
```

---

### Post by amauk on 2011-01-20
> **James78 said:**
> I have the same problem. 4GB of RAM, only 2.99GB being shown.. Using 64 bit.. Quite frustrating.different issue from OP
most likely you have some component (integrated graphics) that's siphoning off your RAM
(although 1Gb seems a bit excessive, but still quick google reveals mobos with 1Gb integrated graphics do exist, so...)

---

### Post by sisco311 on 2011-01-20
> **dlcomm said:**
> Thanks everyone..... since I am one who hates it when people don't  follow up on the posts...  I will try to not do that myself...

I installed the PAE kernel and it now sees the full amount of RAM!   I had a strange issue on the first boot where my glidepad was not working but a proper shutdown and restart of the machine cleared that issue.


Thanks for the feedback!

It seems to me, that the installer didn't detect correctly the amount of RAM. IMO, this is a bug. So, if you have some free time, please report it at [http://bugs.launchpad.net](http://bugs.launchpad.net)

For instructions, see: [uhelp]community/ReportingBugs[/uhelp]

> **dlcomm said:**
> 
I think I will just install the 64bit version in any case but thanks to all for the input and suggestions.

+1 64-bit FTW :)

---

### Post by sisco311 on 2011-01-20
> **amauk said:**
> different issue from OP
most likely you have some component (integrated graphics) that's siphoning off your RAM
(although 1Gb seems a bit excessive, but still quick google reveals mobos with 1Gb integrated graphics do exist, so...)

+1

> **James78 said:**
> I have the same problem. 4GB of RAM, only 2.99GB being shown.. Using 64 bit.. Quite frustrating. :(

free -m for anyone interested
```
             total       used       free     shared    buffers     cached
Mem:          3008       2794        213          0        224       1654
-/+ buffers/cache:        916       2092
Swap:         4692         13       4679
```

I would suggest you to start a new thread. Don't forget to post your hardware specs (I mean your computer's specs :) ).

---

### Post by James78 on 2011-01-20
> **amauk said:**
> different issue from OP
most likely you have some component (integrated graphics) that's siphoning off your RAM
(although 1Gb seems a bit excessive, but still quick google reveals mobos with 1Gb integrated graphics do exist, so...)
Ya, that's what I figured, although as you said, 1GB is really extensive. I'm pretty sure my integrated graphics can't and doesn't eat that much!

---

