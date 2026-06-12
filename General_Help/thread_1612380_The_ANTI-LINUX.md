---
title: "The ANTI-LINUX"
date: 2010-11-03
forum: General Help
---

### Post by ksadil on 2010-11-03
Well I think I have found it, the Shuttle SN78SH7 appears to be the anti-linux.

I bought this little gem as a hot swap spare for my long standing hardy server (web, mail, virtual desktop, print, file, etc)

I put the pieces together, installed lucid and it crashed all over the place. so to fix it I :

(1) upgraded the bios - >still crashing
(2) bought lower spec RAM -> still crashing
(3) added a PCIEx graphics card -> still crashing

(4)Tried Mint - still crashing
(5) tried mint i386 - still crashing
(6) ( ashamed to admit it ) installed W7 -> appears stable
until
(7) tried to run 64 bit lucid in virtualbox ( had to enable  the onboard video card to enable AMD-V, to make 64 bit work) -BSOD - still crashing

I wish I could get my money back.

Support answered one email - 1 week later and has not replied since

Shuttle support forum has not approved my registration so I cannot even post a request for help with the shuttle community.

Shuttle + GeForce8200 -> what a lemon!!!

Please if you own one of these lemons and have any work-arounds, please share.

Looks like I have a new windows gaming machine that I did not actually want :(

---

### Post by Grenage on 2010-11-03
Personally, I'd ask for a refund; it sounds like there are hardware problems.

---

### Post by coffeecat on 2010-11-03
I'm sorry to hear of your problem.

Since Mint is really just Ubuntu with a green face and a few tweaks, why not try a few live CDs from some other distros just to be sure the machine is really anti-Linux rather than just anti-Ubuntu? I have seen threads from people where they could not get Ubuntu to work on a particular machine whereas other distros did.

For an interesting Debian-based distro, try Mepis. Mepis only comes in KDE flavour, but the RPM distros, Opensuse, PCLinuxOS and Fedora all have both gnome as well as KDE versions. Fedora 14 has only just been released and I'm burning the ISO to disc as I write. That might be a good one to try.

Good luck!

---

### Post by ksadil on 2010-11-03
I bought the original case/memory/cpu pieces as online hardware components, and the newer graphics card and memory from a local shop. By the time I courier it back It will only get half the money back on my total spend.

And W7 apps works fine, and they don't actually support linux, so I don't think I have much chance of a refund.

---

### Post by ksadil on 2010-11-03
> **coffeecat said:**
> I'm sorry to hear of your problem.

Since Mint is really just Ubuntu with a green face and a few tweaks, why not try a few live CDs from some other distros just to be sure the machine is really anti-Linux rather than just anti-Ubuntu? I have seen threads from people where they could not get Ubuntu to work on a particular machine whereas other distros did.

For an interesting Debian-based distro, try Mepis. Mepis only comes in KDE flavour, but the RPM distros, Opensuse, PCLinuxOS and Fedora all have both gnome as well as KDE versions. Fedora 14 has only just been released and I'm burning the ISO to disc as I write. That might be a good one to try.

Good luck!


I will give Fredora a try, thanks for the suggestion.

---

### Post by Grenage on 2010-11-03
I might suspect the motherboard; you've changed the memory, and a bad CPU is less likely.  If it works on Windows 7, stress-test it as much as possible from there.

---

### Post by coffeecat on 2010-11-03
> **ksadil said:**
> I will give Fredora a try, thanks for the suggestion.

I'm posting from a freshly-installed Fedora 14 at the moment. It's looking - well - blue. If it works on that Shuttle and you haven't tried Fedora before, you'll find that Fedora is much more restrictive about non-free stuff. Soon fixed though. I find this guide useful:

[http://www.mjmwired.net/resources/](http://www.mjmwired.net/resources/)

The guide for 13 will probably work well enough in 14 until the author gets a 14 guide posted.

---

### Post by ksadil on 2010-11-03
Well I tried ran a stress test (some burnin program) prog in W7 and it fell over alright. So I removed the video card and tried stress test again and it does not fall over. Could it be power related? Please excuse my ignorance, but strong enough to drive 32 bits with the video card,  and without the video card, strong enough to drive W7-64? System draining power from CPU? (just shooting from the hip here)

Would it be worth giving the cpu some more volts in Bios? Or will I fry this thing?

---

### Post by Grenage on 2010-11-03
I would not recommend changing the CPU voltage; it should run fine at stock levels.

Low power is definitely a strong candidate for your problems.  I don't know how much draw there is when burning a CD, but it's probably a reasonable amount.  What rating does your PSU have, and do you possess a spare?

---

### Post by 3Miro on 2010-11-03
I agree, don't mess with the CPU voltage. What are the Video card and CPU and how powerful is the power supply (how many watts).

---

### Post by ksadil on 2010-11-03
300w psu ,

No spare

---

### Post by ksadil on 2010-11-03
from my stress testing software log:
000190| 1030  00000bb4  Nov, 03 - 22:54:23 | Starting Prime Test Module on CPU 3

000191| 1038  00001388  Nov, 03 - 22:54:23 | Starting Memory Mdoule on CPU 3

000192| 1040  00000cec  Nov, 03 - 22:54:23 | Starting HD Module on CPU 3

000193| 1042  00000da0  Nov, 03 - 22:54:23 | Starting MMX Module on CPU 3

000194| 9999  00000ba8  Nov, 03 - 22:57:08 |  Error:CPU 3: Checksums do not match; Matrix1 = -28115503932.883739, Matrix2 = -28115503932.884014

000195| 0000  00000ba8  Nov, 03 - 22:57:08 | Minidump file saved at C:\Program Files (x86)\Hot CPU Tester Pro 4 LE\\HCTNov03-225708.dmp

000000| 0000  00000df0  Nov, 03 - 23:00:15 | Startig Hot CPU Tester Pro 4.4

000001| 1012  00000df0  Nov, 03 - 23:00:16 | Initializing DefectTrack Engine version 2.2.0

000002| 1010  00000df0  Nov, 03 - 23:00:16 | Loading options...

000003| 1011  00000df0  Nov, 03 - 23:00:16 | Reading system info...

000004| 0000  00000df0  Nov, 03 - 23:00:18 |  CPU: AMD Phenom(tm) II X4 965 Processor

000005| 0000  00000df0  Nov, 03 - 23:00:18 |  Speed: 3399MHz

000006| 0005  00000df0  Nov, 03 - 23:00:18 | -1

000007| 0005  00000df0  Nov, 03 - 23:00:18 | 64

000008| 0005  00000df0  Nov, 03 - 23:00:18 | 64

000009| 0000  00000df0  Nov, 03 - 23:00:18 |  L1 Cache Size: 128KB

000010| 0000  00000df0  Nov, 03 - 23:00:18 |  L2 Cache Size: 512KB

000011| 0000  00000df0  Nov, 03 - 23:00:18 |  L3 Cache Size: -1KB

000012| 0000  00000df0  Nov, 03 - 23:00:18 |  Hyper-Threading: FALSE

000013| 0000  00000df0  Nov, 03 - 23:00:18 |  SMP: TRUE

000014| 0000  00000df0  Nov, 03 - 23:00:18 | Scanning SMBIOS...

000015| 0000  00000df0  Nov, 03 - 23:00:18 | Could not read SMBIOS data

000016| 0000  00000df0  Nov, 03 - 23:00:18 |  Total Physical Memory: -135798784 bytes

000017| 0000  00000df0  Nov, 03 - 23:00:18 |  Availabe Physical Memory: -1264377856 bytes

000018| 0000  00000df0  Nov, 03 - 23:00:18 |  Total Virtual Memory: -131072 bytes

000019| 0000  00000df0  Nov, 03 - 23:00:18 |  Availabe Virtual Memory: -106635264 bytes

000020| 0000  00000df0  Nov, 03 - 23:00:18 |  Operating System: Windows Server 2007 Business 

000021| 0156  00000df0  Nov, 03 - 23:00:18 | Setting Process Priority...

000022| 1009  00000df0  Nov, 03 - 23:00:27 | Closing Hot CPU Tester Pro...

000023| 0000  00000df0  Nov, 03 - 23:00:27 | ************ End of Session ************

---

### Post by 3Miro on 2010-11-03
> **ksadil said:**
> 300w psu ,


That is low. Depending on the type of Phenom that you have it will be either 65W or 125W (check with the exact specifications), plus at least 100W for the video + motherboard. If you add another video card, that is another 100W and we are still not counting things like RAM, HDD, CD that can add up to quite a bit.

I am very surprised they would sell anything modern with less then 450W psu. The computer should work if you don't push it, however, I would check to see if you can have it either returned or upgraded to a better psu.

---

### Post by mrnelson1986 on 2010-11-03
This might sound silly, and I didn't really look at the hardware, but are you sure your system supports 64-bit? try the 32-bit?

---

### Post by Grenage on 2010-11-03
It wouldn't work at all if it was an x32 CPU.

I agree with **3Miro**, and would recommend a wore powerful PSU.  Modern processors and graphic cards can draw a surprising amount of juice.  Alternatively, do you really need a dedicated graphics card?

---

### Post by mastablasta on 2010-11-03
LOL... they used to ship 300 W PSU like 10 years ago.
 
you really do need a stronger PSU. 450 W->.
 
the more the better. with good motherboard you wont' be using all power all the time anyway...

---

### Post by ksadil on 2010-11-03
> **mastablasta said:**
> LOL... they used to ship 300 W PSU like 10 years ago.
 
you really do need a stronger PSU. 450 W->.
 
the more the better. with good motherboard you wont' be using all power all the time anyway...

I thought it seemed light but on the box of the shuttle barebone unit "Support AMD phenom cpu" and a picture of a Phenom X4 CPU with 64  in the logo.

The graphics card was bought because I thought ubuntu did not support GeForce 8200 hence mis-diagnosing the crashes.

---

### Post by ksadil on 2010-11-03
> **ksadil said:**
> I thought it seemed light but on the box of the shuttle barebone unit "Support AMD phenom cpu" and a picture of a Phenom X4 CPU with 64  in the logo.

The graphics card was bought because I thought ubuntu did not support GeForce 8200 hence mis-diagnosing the crashes.

And....... it looks like the 300W version is the big one with the standard being 250W :(

Probably won't fit a standard PSU in this SFF box :(

---

### Post by mastablasta on 2010-11-03
i am sorry, but Phenom is not low resource CPU, add a graphics card to this... 300W might be enough for some celeron (AMD has sempron or something) or Atom with some onboard graphics used.
 
are you sure it's 300 W? Do you maybe have [http://global.shuttle.com/SilentX.jsp](http://global.shuttle.com/SilentX.jsp)?
 
Anyway it could be the problem is not in CPU. though it does act like there is a hardware issue. Or maybe they forgot to plug something in.
 
are there any messages when it crashes? you could also check logs (in linux) if you have the linux installed, to see if anything unusual is found there.
 
It might also be that it simply only works with Win7.

---

### Post by coffeecat on 2010-11-03
> **mastablasta said:**
> i am sorry, but Phenom is not low resource CPU

Whoa! Don't confuse high resource with high power consumption.

My 4-core Phenom has a 65W consumption compared with the less-capable twin core Athlon X2 in my previous machine which was 89W.

This year AMD have released 4-core 45nm Phenom IIs with power consumption between 25 and 45W.

@ksadil, Is the Geforce 8200 the onboard graphics or the PCIe graphics? What are the two graphics chipsets that you've got?

With all this focus on the possibility of an inadequate PSU, one thing that hasn't been considered is that the graphics card might be faulty.

---

### Post by Mark Phelps on 2010-11-03
My guess would be that it's a combination of the 300W PSU, the multi-core Phenom -- and the graphics card.

I'm running a 4-core Phenom with onboard ATI HD3200 graphics -- and it can run all day without any problems.  And, I have a 300W PSU in the box. 

But, maybe the onboard version of the graphics chip demands less power?

---

### Post by ksadil on 2010-11-03
Here are the specs: 

[http://global.shuttle.com/product_detail_spec.jsp?PI=939](http://global.shuttle.com/product_detail_spec.jsp?PI=939)

300W PSU and GeForce8200 chriset

I now have the graphics card out, and I am going to run a test with every unnecesary power demand disables, set the cpu stepping to 800mHz and run a see if it becomes stable.

---

### Post by ksadil on 2010-11-03
it appears to be stable at 800MHz

---

### Post by Butthead on 2010-11-03
Hmm, I'm posting this just fine from my Shuttle SN27P2 Athlon 64 4600+ X2 which also has the 300w PSU in it. :confused:

Got all kinds of secondary processes running in the background right now too with no problems. :guitar:

---

### Post by ksadil on 2010-11-04
This one has been running for 6 hours now on 800MHz. I just bumped it up to 2.2GHz. See how that goes.

All of my flashplayer crashing problems seem to be gone with the lower clock speed settings.

---

### Post by ksadil on 2010-11-04
When I turn it up to 2200 I get pulse audio crashing. From Var/log/messages:
Nov  4 15:34:54 mint64 kernel: [ 1930.241462] Pid: 1845, comm: pulseaudio Tainted: P           2.6.32-21-generic #32-Ubuntu SN78S
Nov  4 15:34:54 mint64 kernel: [ 1930.241465] RIP: 0010:[<ffffffff8145699d>]  [<ffffffff8145699d>] __skb_recv_datagram+0x9d/0x290
Nov  4 15:34:54 mint64 kernel: [ 1930.241473] RSP: 0018:ffff880115b4bd58  EFLAGS: 00010002
Nov  4 15:34:54 mint64 kernel: [ 1930.241475] RAX: 0000000000000282 RBX: ffff880115b99200 RCX: 0000000000000000
Nov  4 15:34:54 mint64 kernel: [ 1930.241477] RDX: 7bff880115b992b0 RSI: 0000000000000282 RDI: ffff880115b992c4
Nov  4 15:34:54 mint64 kernel: [ 1930.241479] RBP: ffff880115b4bdf8 R08: ffffffff815b5e40 R09: 00000000000000c0
Nov  4 15:34:54 mint64 kernel: [ 1930.241481] R10: 0000000000000000 R11: 0000000000000000 R12: ffff880115b992b0
Nov  4 15:34:54 mint64 kernel: [ 1930.241483] R13: ffff880115b4bd98 R14: ffff880115b4bdb0 R15: ffff880115b992c4
Nov  4 15:34:54 mint64 kernel: [ 1930.241485] FS:  00007fc2c447e740(0000) GS:ffff880028280000(0000) knlGS:0000000000000000
Nov  4 15:34:54 mint64 kernel: [ 1930.241488] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Nov  4 15:34:54 mint64 kernel: [ 1930.241489] CR2: 00007fb9cc1ba000 CR3: 000000010e55d000 CR4: 00000000000006e0
Nov  4 15:34:54 mint64 kernel: [ 1930.241491] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Nov  4 15:34:54 mint64 kernel: [ 1930.241493] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Nov  4 15:34:54 mint64 kernel: [ 1930.241496] Process pulseaudio (pid: 1845, threadinfo ffff880115b4a000, task ffff88010e76dbc0)
Nov  4 15:34:54 mint64 kernel: [ 1930.241499]  ffffffff811549d0 ffff880115b9934c ffff88010e76dbc0 7fffffffffffffff
Nov  4 15:34:54 mint64 kernel: [ 1930.241502] <0> ffff880115b4be34 ffff880115b4be14 0000000015b4bdd8 ffff88010e76dbc0
Nov  4 15:34:54 mint64 kernel: [ 1930.241505] <0> ffff880115b4bda8 ffffffff81540c9e ffff880115b4bdc8 ffffffff81179626
Nov  4 15:34:54 mint64 kernel: [ 1930.241514]  [<ffffffff811549d0>] ? pollwake+0x0/0x60
Nov  4 15:34:54 mint64 kernel: [ 1930.241518]  [<ffffffff81540c9e>] ? _spin_lock+0xe/0x20
Nov  4 15:34:54 mint64 kernel: [ 1930.241522]  [<ffffffff81179626>] ? inotify_d_instantiate+0x56/0x70
Nov  4 15:34:54 mint64 kernel: [ 1930.241525]  [<ffffffff81456bb4>] skb_recv_datagram+0x24/0x30
Nov  4 15:34:54 mint64 kernel: [ 1930.241529]  [<ffffffff814dffb4>] unix_accept+0x74/0x120
Nov  4 15:34:54 mint64 kernel: [ 1930.241533]  [<ffffffff8144ca46>] sys_accept4+0x196/0x300
Nov  4 15:34:54 mint64 kernel: [ 1930.241536]  [<ffffffff81154cba>] ? sys_ppoll+0x7a/0x180
Nov  4 15:34:54 mint64 kernel: [ 1930.241539]  [<ffffffff8144cbc0>] sys_accept+0x10/0x20
Nov  4 15:34:54 mint64 kernel: [ 1930.241543]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
Nov  4 15:34:54 mint64 kernel: [ 1930.241571]  RSP <ffff880115b4bd58>
Nov  4 15:34:54 mint64 kernel: [ 1930.241574] ---[ end trace d85e87bb1c7880d0 ]---

---

### Post by ksadil on 2010-11-04
How can I set Ubuntu to start at 800MHz without me having to use the frequency scaling applet?

---

### Post by mastablasta on 2010-11-04
Ok what about your CPU temp. is it normal? it could be that linux cranks up the CPU or doesn't manage the heating correctly and therefore crashes the computer.
 
> **coffeecat said:**
>  
With all this focus on the possibility of an inadequate PSU, one thing that hasn't been considered is that the graphics card might be faulty.
 
Does not explain the fact that it works in Win7
 
faulty drivers then?

---

### Post by linux18 on 2010-11-04
use the psu from your old computer, they are most likely all ATX and cross compatible. If your old computer's PSU is > 300 watts try it and see haw it goes.

P.S. try a memtest as well

---

### Post by cascade9 on 2010-11-04
I'd say its almost certainm that you havent got a big enough power supply. 

I recently built a machine for my housemate, Phenom II X2 550 (80watts TDP), AMD 770 chipset motherboard, 8400GS, 4GB DDR3, Pioneer DVD-RW and a 1TB WD green power drive. The person who asked me to build it 'didnt have enough money for a new power supply' and wanted to run an (slightly old but with minimal use) Thermaltake 430watt power supply. Result? Constant segfaults. 

In the end, I put the motherboard/CPU/RAM into my case, running with my Corsair 520HX and my 8600GT, Asus (OK, pioneer rebranded) SATA DVD-RW and 1TB WD drive. 

I ended up doing a trade/buy of those parts so I've been running the setup for a few weeks, runs very well, not a single crash/segfualt yet. 

> **Mark Phelps said:**
> My guess would be that it's a combination of the 300W PSU, the multi-core Phenom -- and the graphics card.

I'm running a 4-core Phenom with onboard ATI HD3200 graphics -- and it can run all day without any problems. And, I have a 300W PSU in the box. 

But, maybe the onboard version of the graphics chip demands less power?

Onboard does tend to use les power than a standalone card. 

I'd also like to say that not all 300watt power supples are created equal. Older power supplies have proportionally more amps on the 3.3v and 5v lines, newer power suplies have more AMPs for 12v. Also, some of the power supplies out there have, and I kid you not, a  sticker on the side saying whatever the manufactuer thinks people want.....not what can actually be delivered.  

It could be that you've got a newer power supply (with higer 12v rail) and its actually can deliver 300watts, where shuttle has used junk. 

> **coffeecat said:**
> Whoa! Don't confuse high resource with high power consumption.

My 4-core Phenom has a 65W consumption compared with the less-capable twin core Athlon X2 in my previous machine which was 89W.

This year AMD have released 4-core 45nm Phenom IIs with power consumption between 25 and 45W.

@ksadil, Is the Geforce 8200 the onboard graphics or the PCIe graphics? What are the two graphics chipsets that you've got?

With all this focus on the possibility of an inadequate PSU, one thing that hasn't been considered is that the graphics card might be faulty.

Umm....Phenom X4 @ 65watts? (BTW, thats TDP, not consumption) 

None of the retail Phenom II X4s are 25-45watts TDP, the lowest I've ever sen is 65watts TDP (for the X4 905e and 910e, which are special "energy efficient" models run much lower clockspeeds). AMD doesnt seem to list any 25-45watt TDP models either-

[http://www.amd.com/us/products/desktop/processors/phenom-ii/Pages/phenom-ii-model-number-comparison.aspx](http://www.amd.com/us/products/desktop/processors/phenom-ii/Pages/phenom-ii-model-number-comparison.aspx)

Unless you are talking mobile CPUs, then there are 25-45watt models....not that you'll find any S1G4 (AMDs  curerent mobile socket) desktop motherboards, so that is a moot point anyway.

---

### Post by ksadil on 2010-11-04
I am inclined to agree with the power supply verdict :( . I do not think larger PSU's this small form factor machine are not going to be easy to find. For now I can run it at 800MHz for the server purpose intended, while I hunt around for larger PSU's that will fit this case.

---

### Post by coffeecat on 2010-11-04
> **coffeecat said:**
> With all this focus on the possibility of an  inadequate PSU, one thing that hasn't been considered is that the  graphics card might be faulty.

> **mastablasta said:**
> Does not explain the fact that it works in Win7

This sounds like a problem with the graphics card in W7:

> **ksadil said:**
> Well I tried ran a stress test (some burnin program) prog in W7 and it fell over alright. So I removed the video card and tried stress test again and it does not fall over.

Power issue? Too much heat in a small form factor? Faulty card? Who knows?

---

### Post by ksadil on 2010-11-04
> **coffeecat said:**
> This sounds like a problem with the graphics card in W7:



Power issue? Too much heat in a small form factor? Faulty card? Who knows?

sorry I mean't to mention, no overheating problems. It stays cool right up to crash

---

### Post by ksadil on 2010-11-04
Just trying some other configurations, running just one core (noapic, nolapic) seems stable too and actually seems much faster than 4 cores at 800MHz. There appears to be a 500W PSU available, but my CPU is certified by Shuttle to run on the 300W PSU. I guess my PUS may be faulty, but how would you prove it?

---

### Post by 3Miro on 2010-11-04
When they have specifications like "minimum XXXW PSU" or certified for such and such CPU, they cannot cover all the ground. Power consumption is the sum total of everything in the box, not just the CPU and Video card (although they are usually the biggest hogs). I had a 500W PSU that said SLI certified, however, it definitely could no run 2xGF8800GTS, it could run lower spec cards in SLI mode. Basically certified for the shuttle probably assumes some base defaults, now whatever upgrades you have.

From what I read, 300W is too small and it looks like that is the problem, since lowering CPU frequency and turning off cores seems to work.

---

### Post by ksadil on 2010-11-04
> **3Miro said:**
> When they have specifications like "minimum XXXW PSU" or certified for such and such CPU, they cannot cover all the ground. Power consumption is the sum total of everything in the box, not just the CPU and Video card (although they are usually the biggest hogs). I had a 500W PSU that said SLI certified, however, it definitely could no run 2xGF8800GTS, it could run lower spec cards in SLI mode. Basically certified for the shuttle probably assumes some base defaults, now whatever upgrades you have.

From what I read, 300W is too small and it looks like that is the problem, since lowering CPU frequency and turning off cores seems to work.

hmmm.. the only thing I could extract from this box is a memory stick (since I have 2 x 2G sticks installed) and the cpu is hardware certified. I have no cdrom, no graphics card, no sound, card, nothing. Looks like faulty components or at least misleading marketing materials to me :(

---

### Post by 3Miro on 2010-11-04
> **ksadil said:**
> Looks like faulty components or at least misleading marketing materials to me :(

If the system is that barren then it may indeed be a faulty component. Can you borrow a more powerful PSU from someone to try if the system will work better (and I guess this also includes you being savvy enough to connect it, also there may be warranty issues if you open the box).

---

### Post by ksadil on 2010-11-05
Well I plugged in a 600W PSU and I can concurrently:

(1) run a 64 bit virtual machine
(2) play a youtube clip
(3) rip a dvd

Rock Solid

Thanks,
Guys

---

### Post by 3Miro on 2010-11-05
> **ksadil said:**
> Well I plugged in a 600W PSU and I can concurrently:

(1) run a 64 bit virtual machine
(2) play a youtube clip
(3) rip a dvd

Rock Solid

Thanks,
Guys

My guess is that the old PSU was insufficient for power, however, it may be the case that 300W was enough, however, the PSU itself was defective.

---

### Post by ibizatunes on 2010-11-05
boot to ubuntu live cd and do a memory check on your computer

---

### Post by Grenage on 2010-11-05
See if you can return it.  It's possible that the PSU was sold with only the bare equipment in mind - but that's a raw deal.

Glad you got it resolved.

---

### Post by ksadil on 2010-11-05
I spoke too soon. I get occasional lockups in Lucid, and occasional BSOD in W7. This is at full speed, and I think it might be different problems.

BSOD on windows was running an XP 3d game (RealFlight)

Lucid locked up while installing apps from Ubuntutweaks.

This machine scores top 10 in hardinfo benchmarks (sometimes 1st and 2nd place). I am running AMD-64,ow stable would you expect it to be for video and gaming??

---

### Post by Grenage on 2010-11-05
I would expect any system to be stable, instability points to hardware problem or bad software; I think we can rule out software.

---

### Post by 3Miro on 2010-11-05
> **ksadil said:**
> I spoke too soon. I get occasional lockups in Lucid, and occasional BSOD in W7. This is at full speed, and I think it might be different problems.

BSOD on windows was running an XP 3d game (RealFlight)

Lucid locked up while installing apps from Ubuntutweaks.

This machine scores top 10 in hardinfo benchmarks (sometimes 1st and 2nd place). I am running AMD-64,ow stable would you expect it to be for video and gaming??

If the machine locks up using windows (specifically BSOD) then you have a hardware issue. You should contact the manufacturers and return/replace the item. They probably sold it for you with windows in mind (like most hardware), so you will be at your full right to demand it fixed. Also, as a general rule, don't tell them that you have been using Linux on it, they may say that you broke the machine with Ubuntu (which is ridiculous but some manufacturers/vendors will do anything to weasel out of a warranty). Just say, "Here it is, it isn't working" and point to the BSOD examples under windows.

---

### Post by ksadil on 2010-11-05
Teah, I don't think that argument will work, they will say buy the upgraded version of realflight that is approved for W7.

---

### Post by coffeecat on 2010-11-05
> **ksadil said:**
> Teah, I don't think that argument will work

I don't know what consumer law is like in your part of the world, but over here we have consumer rights, and I'm sure you have too. Exercise them. You have been sold faulty hardware.

---

### Post by ubudog on 2010-11-05
> **Grenage said:**
> Personally, I'd ask for a refund; it sounds like there are hardware problems.

I agree.

---

### Post by DirtyPC on 2010-11-05
> **3Miro said:**
> That is low. Depending on the type of Phenom that you have it will be either 65W or 125W (check with the exact specifications), plus at least 100W for the video + motherboard. If you add another video card, that is another 100W and we are still not counting things like RAM, HDD, CD that can add up to quite a bit.

I am very surprised they would sell anything modern with less then 450W psu. The computer should work if you don't push it, however, I would check to see if you can have it either returned or upgraded to a better psu.
And ive got 4gb ram, 2 dvd players, a graphics card, + amd phenom x4 945 hooked up to a 250w psu! And it runs fine!!!!

---

### Post by Butthead on 2010-11-05
Yeah, like I said, I have 2 HD's, floppy, DVD writer plus a bunch of USB lamps and crap connected to my 300 watt PSU Shuttle with no problems.

---

### Post by ksadil on 2010-11-06
Well before the 600WPSU I could crash my box at will, by loading the cpu up

Today I ran a mem test (again) this time it found errors. So I tested 1 stick, then the other then both again and now no errors. I guess they weren't seated properly  (does that happen or is a gremlin lurking???)

Anyway, now I cannot crash linux (Lucid 64)...at last :)

and the only way I can crash W7 is to play a 3d game in multiplayer mode. I suspect this is a W7 issue, not a hardware issue as the software was made for XP and many other gamers are getting this dxgmms BSOD according to google. 

I am now ordering a 500W PSU that fits inside the case.

---

### Post by cascade9 on 2010-11-07
@ Butthead + harrylucas1- just becaquse it runs for you, doesnt mean it will for others. Maybe your not loading up your CPUs to 100%, maybe you've got better quality power supplies, maybe *lots and lots of things*. 

BTW, 3Miro is in some ways overstating the power consumption. That said, I still wouldnt be running a X4 965 on a 250 or 300 watt power supply.... 

[http://www.xbitlabs.com/articles/cpu/display/power-consumption-overclocking.html](http://www.xbitlabs.com/articles/cpu/display/power-consumption-overclocking.html)

[http://www.xbitlabs.com/articles/video/display/htpc-graphics-cards_4.html](http://www.xbitlabs.com/articles/video/display/htpc-graphics-cards_4.html)

> **ksadil said:**
> Today I ran a mem test (again) this time it found errors. So I tested 1 stick, then the other then both again and now no errors. I guess they weren't seated properly  (does that happen or is a gremlin lurking???)

Yes, that (badly seated RAM sticks) can cause errors. That could explain things, depending on how long the RAM hasntr been seated properly for. 

Then again, it could be that you've got an intermittent fault....which can be almost impossible to track down, I'm sorry to say.

---

### Post by ksadil on 2010-11-07
I got curious, and put back my 300W PSU after reseating the Memory sticks, and now it is still rock solid with that as well.

That is so annoying that the first time I ran the memtest back on the 300W PSU, it passed. It was only later with the big PSU, the memtest  failed.

Maybe it was the mem sticks all along. This has been one painful exercise, but it sure is good to have a stable system.

Now it is not an antilinux system but a perfect match......eat my words

---

### Post by Butthead on 2010-11-07
> **cascade9 said:**
> @ Butthead + harrylucas1- just becaquse it runs for you, doesnt mean it will for others. Maybe your not loading up your CPUs to 100%, maybe you've got better quality power supplies, maybe *lots and lots of things*. 


I just stated that I have a Shuttle with a 300W PSU in it.

I don't think Shuttle makes too many different PSU's for their mini footprint systems.

I personally think that people have "big block engine" syndrome when it comes to PSU's.  Can only go 75 MPH at the most, but still want a 450 HP engine. 

And yes, I got a bunch of crap hanging off of it on USB with no crashes (so far).

---

### Post by ksadil on 2010-11-07
> **Butthead said:**
> I just stated that I have a Shuttle with a 300W PSU in it.

I don't think Shuttle makes too many different PSU's for their mini footprint systems.

I personally think that people have "big block engine" syndrome when it comes to PSU's.  Can only go 75 MPH at the most, but still want a 450 HP engine. 

And yes, I got a bunch of crap hanging off of it on USB with no crashes (so far).

Actually shuttle does make some bigger PSU's for the SFF box but it is not necessarily easy to find them by browsing their web site. My 500W is on order. I am not really sure that I need it now.

---

### Post by Butthead on 2010-11-08
> **ksadil said:**
> Actually shuttle does make some bigger PSU's for the SFF box but it is not necessarily easy to find them by browsing their web site. My 500W is on order. I am not really sure that I need it now.

Well, you do have the extra horsepower now if you ever need it. :)

You can always do an experiment to see how many external peripherals you can chain load off of it now before it crashes this time. :P

USB coffee cup warmer, anyone?:mrgreen:

---

### Post by cascade9 on 2010-11-12
> **Butthead said:**
> I just stated that I have a Shuttle with a 300W PSU in it.

Which I took as a 'it works for me'. 

If thats not what you meant, then I'm confused. 

> **Butthead said:**
> I personally think that people have "big block engine" syndrome when it comes to PSU's.  Can only go 75 MPH at the most, but still want a 450 HP engine. 

And yes, I got a bunch of crap hanging off of it on USB with no crashes (so far).

Depends on the system. Considering the power draw of the X4 965 CPU, IMO a 250 or 300 wat power supply is just to small. If it was a Athlon II X2 2XXe, 250watts is tons. 

BTW, USB 2.0 has a (theoretical) max power draw of 2.5watts. Most devices use far, far less. If a device requires more than 2.5watts, it needs multipule USB connectors. You'd need a LOT of USB devices @ max power to use much power at all......2.5watts is virtually nothing.

---

### Post by Grenage on 2010-11-12
> **cascade9 said:**
> BTW, USB 2.0 has a (theoretical) max power draw of 2.5watts. Most devices use far, far less. If a device requires more than 2.5watts, it needs multipule USB connectors. You'd need a LOT of USB devices @ max power to use much power at all......2.5watts is virtually nothing.

Indeed.  Power issues where USB concerned are generally down to a board that can't provide enough power, rather than a PSU being unable to deliver it.  If power was that much of an issue, then a CPU spike would topple the tower.

---

### Post by Butthead on 2010-11-12
> **cascade9 said:**
> Which I took as a 'it works for me'. 

If thats not what you meant, then I'm confused. 

Depends on the system. Considering the power draw of the X4 965 CPU, IMO a 250 or 300 wat power supply is just to small. If it was a Athlon II X2 2XXe, 250watts is tons.

I would think the Shuttle engineers would take into account what PSU they are sticking into a system according to what motherboard & how many slots it has built into it.

---

### Post by cascade9 on 2010-11-13
> **Butthead said:**
> I would think the Shuttle engineers would take into account what PSU they are sticking into a system according to what motherboard & how many slots it has built into it.

You might think that......

A Phenom II X4 965 + ATI 5870 can use over 350watts at max draw. The 5870 isnt even that much of a power pig, a GTX480 would push that figure up a huge amount. 

I dont know if a GTX480, or even a 5870 will fit into the shuttle case. If they did, then 300watts is nowhere near enough power. 

Shuttle might be assuming that people will use the onboard 8200. But since its got a PCIe slot, with the logic your using, it should be fine even with a video card + X4 965. 300watts could well 'let the magic smoke out' with the 'right' (or wrong)  parts. 

Shuttle has probably wacked a 300watt PSU in because thats what they have. Thats fairly typical of 'corporate' manufactuers.

---

### Post by kuvanito on 2010-11-13
actually these machines run great in all architectures
glad you got it all worked out,happy linux!

---

### Post by Butthead on 2010-11-13
Well, you do have to use a little common sense...;)

But, (like you pointed out), I don't even think a GTX480 would even fit in a Shuttle mini box.

The EVGA GeForce 7950 GT I have in mine right now (flat as a board) was even a shoehorn fit to get installed. #-o 

But yeah, you're right.  Someone will manage to stick the wrong card in. :eek:

---

### Post by ksadil on 2010-12-18
I am back to all onboard components, but finally added an optical drive instead of the external dvd burner. Very stable, but sometimes it more than 3 minutes to bring up gdm. other times 30 seconds. noapic/nolapic do work but at the cost of performance (?)

---

