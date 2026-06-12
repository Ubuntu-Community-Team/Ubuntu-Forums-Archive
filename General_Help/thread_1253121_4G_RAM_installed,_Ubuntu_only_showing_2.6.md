---
title: "4G RAM installed, Ubuntu only showing 2.6"
date: 2009-08-29
forum: General Help
---

### Post by traynor on 2009-08-29
I have 2 2GB chips in my HP DV6000 laptop, and when I look at the System Monitor it shows only 2.6 G of Memory.

Why is that?

---

### Post by NoaHall on 2009-08-29
Are you running 64 bit or 32 bit?

---

### Post by jerome1232 on 2009-08-29
And what does your bios say about how much ram you have.

---

### Post by Lrno on 2009-08-29
As far as I know, if you are running a 32-bit distro, the OS can only allocate up to 4Gb of memory. That is 4 Gb total considering your RAM **and** your Swap memory. (Anybody correct me if I am wrong)

If this is the case, you probably have 1.4Gb of Swapping memory.
What you can do is, get rid of the Swap partition and work only with your RAM memory.

Hope this helps with your problem. :)

---

### Post by NoaHall on 2009-08-29
Swap has nothing to do with ram, you can have as much swap as you want ;)
The maximum ram under 32 bit is around 3.4 Gb
Under 64bit, there's no such limit, as it is much higher

---

### Post by jerome1232 on 2009-08-29
Yeah, swap doesn't come into play.

32bit can address up to 4gb of memory, every device on your system must be addressable as well so usually you only get about 3.4 GB of addressable ram.

---

### Post by overdrank on 2009-08-29
Also remember the integrated graphics will be allocated some.:)

---

### Post by traynor on 2009-08-29
> **NoaHall said:**
> Are you running 64 bit or 32 bit?

It was that question that prompted me to look at my machine's specs. I have an AMD Turion 64X2 - how do I check in Ubuntu 9.0.4 to see if I'm running 32 or 64 bit?

---

### Post by jerome1232 on 2009-08-29
uname -m

---

### Post by traynor on 2009-08-29
> **jerome1232 said:**
> uname -m

linux@daedelus:~$ uname -m
i686
linux@daedelus:~$ 


is 686 the 64bit version?

---

### Post by jerome1232 on 2009-08-29
686 is 32bit

x86_64 is 64 bit

I guess I should have mentioned that :)

---

### Post by traynor on 2009-08-29
> **jerome1232 said:**
> And what does your bios say about how much ram you have.

I restarted (wow Linux is fast!) and checked the BIOS which shows 4096M of memory. So why doesn't it show in System Monitor? Would it have to do with the dual-boot partition where I also have Windows on this machine?

Also, in the System Monitor it's showing both AMD processors 0: and 1: (both say AMD 64 X2

SM also shows I'm running Kernel Linux 2.6.28-15-generic, GNOME 2.26.1

---

### Post by traynor on 2009-08-29
> **jerome1232 said:**
> 686 is 32bit

x86_64 is 64 bit



So if I have 686 am I using my dual processor and ram to their fullest?

Is there a way to modify or upgrade my ubuntu install to be running the 64-bit version?

---

### Post by GSF1200S on 2009-08-29
> **traynor said:**
> So if I have 686 am I using my dual processor and ram to their fullest?

Is there a way to modify or upgrade my ubuntu install to be running the 64-bit version?

No, as they said youd need to install the AMD64 version of Ubuntu to use all the RAM and processor you have. You wont really notice, unless you do RAM intensive things.

Linux is very effecient with RAM. Sorry for the bad news :(

**EDIT** You will notice a good boost in video encoding using 64 bit. Otherwise it wont matter much.

---

### Post by jerome1232 on 2009-08-29
Multiple things come into play here, but having multiple Operating Systems won't have an affect on how much ram each one can see.

A) You are using a 32 bit OS which restricts you to about 3.4 GB Ram,

B) It really sounds like you have an integrated graphics which borrows from system ram and uses it as video ram.



The only way to get a 64 bit Ubuntu is to download the 64 bit version and reinstall.

What graphics card are you using btw.

---

### Post by traynor on 2009-08-29
> **jerome1232 said:**
> Multiple things come into play here, but having multiple Operating Systems won't have an affect on how much ram each one can see.

A) You are using a 32 bit OS which restricts you to about 3.4 GB Ram,

B) It really sounds like you have an integrated graphics which borrows from system ram and uses it as video ram.



The only way to get a 64 bit Ubuntu is to download the 64 bit version and reinstall.

What graphics card are you using btw.

What is the command line to show the graphics card I'm using?

Also? Is there a command line I can use to upgrade to 64bit version or do I have to perform a complete reinstall from CD?

---

### Post by inobe on 2009-08-29
```
lspci
```

show it all including graphics

---

### Post by traynor on 2009-08-30
> **inobe said:**
> ```
lspci
```

show it all including graphics

Ok I will check

---

### Post by bboston7 on 2009-08-30
> **traynor said:**
> What is the command line to show the graphics card I'm using?

Also? Is there a command line I can use to upgrade to 64bit version or do I have to perform a complete reinstall from CD?

You're going to have to reinstall.

---

### Post by unix4linux on 2009-08-30
I am having a similar issue except that I did install the x86_64 9.04 Ubuntu on my computer.  I have 4GB of RAM but it only shows:


# free -m
             total       used       free     shared    buffers     cached
Mem:          3935       3901         34          0         54       3107
-/+ buffers/cache:        739       3196
Swap:         1608          0       1608

Now, it's not that much that it's missing so I am ok with it.  My video card has it's own memory so it shouldn't be taking any from RAM either.

My kernel, though, is a generic kernel:

uname -a
Linux sunubuntu 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux

I was under the impression that the Ubuntu install should have picked up that it is an AMD Processor 64 bit and install the correct processor entry in the kernel and then my output from 'uname' would reflect that it is an AMD kernel (At least RedHat/CentOS does).

Then again, my workstation is a Sun W2100z so perhaps that could be part of the problem with it not capturing all of my memory.

Or, maybe I need to have a PAE enabled kernel?  I don't see why this would be necessary if I am running 64bit, though.

Any thoughts?

---

### Post by NoaHall on 2009-08-30
> **unix4linux said:**
> 

uname -a
Linux sunubuntu 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux



It is 64 bit, the "x86_64" indicates that. Where you ram has gone, is due to the fact that they sell things in BYTES and not BITS, so you have 4giga-BYTES, but it's really somewhere around 3.9 giga-BITS

bytes != bits

---

### Post by P4man on 2009-08-30
> **NoaHall said:**
> It is 64 bit, the "x86_64" indicates that. Where you ram has gone, is due to the fact that they sell things in BYTES and not BITS, so you have 4giga-BYTES, but it's really somewhere around 3.9 giga-BITS

bytes != bits

actually, with RAM, 4GB usually means 4096 Mbyte. Then again, probably not with Sun :p. BIOS may also make a hole, reducing the amount of RAM the OS sees, but this not a gigabyte vs gibibyte thing. Then the difference would be much bigger. you get that when you buy a 1TB drive, expecting 1000 Megabyte, only to find out its like 860 Mb formatted.

[http://en.wikipedia.org/wiki/Binary_prefixes#Suggestions_for_new_prefixes](http://en.wikipedia.org/wiki/Binary_prefixes#Suggestions_for_new_prefixes)
[http://en.wikipedia.org/wiki/Binary_prefixes#Deviation_between_binary_and_decimal_interpretations](http://en.wikipedia.org/wiki/Binary_prefixes#Deviation_between_binary_and_decimal_interpretations)

---

### Post by NoaHall on 2009-08-30
I think you mean

Gigabyte vs gigabit
 Expect = Buy a 1TB and see 1000 GB, instead see 880 GB

---

### Post by P4man on 2009-08-30
no, a byte is always 8 bit.

1 Gigabyte =  1.000.000.000 bytes. Thats what they use  when they sell you a harddrive :). 

A gibibyte is 2^30 bytes. So its 1.073.741.824 bytes
A gibibyte (GiB) is 1024 mebibytes (MiB). (a mebibyte being 1024 kibibytes (KiB))

Granted, this binary multiple is not popular, but its what computers use. Hence the confusion when ppl buy a terrabyte drive and discover their PC only sees 900- something "megabyte" (mebibyte actually), which is reduced to even less after partitioning and formatting. In practice often not even 900 MiB.

---

### Post by NoaHall on 2009-08-30
........ I  know fully well that a bit is not a byte! I know how a computer works! That is not what I was saying at all! You're arguing something I said!

---

### Post by P4man on 2009-08-30
Keep your hat on mate :)

you said this:
"so you have 4giga-BYTES, but it's really somewhere around 3.9 giga-BITS"

Probably a typo or brainfart, but I thought Id correct it ;) (even though you must know a lot more than me if you really know how a computer works).

---

### Post by jerrrys on 2009-08-30
> **traynor said:**
> I have 2 2GB chips in my HP DV6000 laptop, and when I look at the System Monitor it shows only 2.6 G of Memory.

Why is that?
  can you compare with another version or distro?  this is a reoccurring discussion.  some people find a fix and some do not...try the server (32bit) kernel or go 64 bit...

---

### Post by unix4linux on 2009-08-30
> Then again, probably not with Sun . BIOS may also make a hole, reducing the amount of RAM the OS sees

Thanks for the replies.  Well, as I mentioned, with other OS', it does see the full 4096.  Only Ubuntu doesn't which is why I was wondering.  It's not a big deal since it's only about 100M or so but if it could be corrected, I wouldn't mind doing so either ;)

---

### Post by P4man on 2009-08-30
> **unix4linux said:**
> Thanks for the replies.  Well, as I mentioned, with other OS', it does see the full 4096.  Only Ubuntu doesn't which is why I was wondering.  It's not a big deal since it's only about 100M or so but if it could be corrected, I wouldn't mind doing so either ;)

Oh, I missed that. I remember reading in someone else's dmesg a message that he didn't have something enabled in BIOS (memory hole?, dont remember) and the kernel message stated something like "this will cost you 64Mb Ram".

have a look in dmesg if you see something similar?

edit: found the message. **Your BIOS doesn't leave a aperture memory hole" and "This costs you 64 MB of RAM".**
If you'd have the same, it might explain half your loss already :)

---

### Post by dj-toonz on 2009-08-30
I had the same problem in till I read up about a PAE kernel that lets you run a 32 bit OS with more then 4 gigs of ram up to 64 gig's of ram (i know fedora 11 has it has default) but haven't been able to enable in jaunty yet, if anyone's using the PAE kernel with jaunty, how do u enable it? and will the nvidia drivers work with it, found it out now. if you want to use a 32 bit OS with more then 4 gigs of ram heres the solution 

[http://ubuntuforums.org/showthread.php?t=855511](http://ubuntuforums.org/showthread.php?t=855511)

---

### Post by unix4linux on 2009-08-30
> Oh, I missed that. I remember reading in someone else's dmesg a message that he didn't have something enabled in BIOS (memory hole?, dont remember) and the kernel message stated something like "this will cost you 64Mb Ram".

have a look in dmesg if you see something similar?

edit: found the message. Your BIOS doesn't leave a aperture memory hole" and "This costs you 64 MB of RAM".
If you'd have the same, it might explain half your loss already 

Looks like I don't have that issue except that it may be using 64MB for something else?  Am I reading that correctly?

Checking aperture...
[    0.004000] AGP bridge at 08:00:00
[    0.004000] Aperture from AGP @ d8000000 old size 32 MB
[    0.004000] Aperture from AGP @ d8000000 size 128 MB (APSIZE f20)
[    0.004000] Node 0: aperture @ d8000000 size 128 MB
[    0.004000] Node 1: aperture @ d8000000 size 128 MB
[    0.004000] Memory: 4020720k/6291456k available (4749k kernel code, 2098292k absent, 171480k reserved, 2523k data, 532k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1

 agpgart-amd64 0000:08:00.0: AGP aperture is 128M @ 0xd8000000
[    0.409908] init_memory_mapping: 00000000d8000000-00000000e0000000
[    0.409911]  00d8000000 - 00e0000000 page 2M
[    0.409920] last_map_addr: e0000000 end: e0000000
[    0.409921] PCI-DMA: using GART IOMMU.
[    0.409924] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture

root@sunubuntu:/home/gvalentin# free -m
             total       used       free     shared    buffers     cached
Mem:          3935       3898         37          0         81       2667
-/+ buffers/cache:       1148       2787
Swap:         1608          0       1608

---

### Post by chriskin on 2009-08-30
> **Lrno said:**
> As far as I know, if you are running a 32-bit distro, the OS can only allocate up to 4Gb of memory. That is 4 Gb total considering your RAM **and** your Swap memory. (Anybody correct me if I am wrong)

If this is the case, you probably have 1.4Gb of Swapping memory.
What you can do is, get rid of the Swap partition and work only with your RAM memory.

Hope this helps with your problem. :)

you mean ram and graphics card memory :)

---

### Post by traynor on 2009-08-30
> **inobe said:**
> ```
lspci
```

show it all including graphics

linux@daedelus:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
linux@daedelus:~$ 

What do you make of this, and is anything in it affecting my RAM usage?

I understand I'll have to re-install the 64-bit version.

---

### Post by traynor on 2009-08-30
> **bboston7 said:**
> You're going to have to reinstall.

Figured as much. That's fine by me...I'm currently dual-booting with Windows Vista. I'll happily wipe it away for good, once I'm comforatable with Linux, which I pretty much am at this point. It's awesome!

---

### Post by Lrno on 2009-08-31
> **chriskin said:**
> you mean ram and graphics card memory :)

Actually I'm sorry for my mistake but I'm sure that I have read that about the swap memory when I was searching for this precise problem a couple of months ago. 
What's more, I'm pretty sure I've read it in this forum, I should look for the post.
In any case, I'm really new with Kubuntu and I was just trying to help :) that's why I ask to correct me if I was wrong.

Hope I did not cause any trouble with my post.

Lrno.

---

