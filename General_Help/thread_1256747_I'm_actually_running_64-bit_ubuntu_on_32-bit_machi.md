---
title: "I'm actually running 64-bit ubuntu on 32-bit machine"
date: 2009-09-03
forum: General Help
---

### Post by shakeham on 2009-09-03
After installation and Ubuntu is working great. However now I noticed I installed from the wrong CD-- this is a 64-bit CD and this machine is 32-bit. It amazes me Ubuntu just runs smoothly and doesn't complain about anything

My question is, is this a problem? Do I need to worry about it?

If I compile a fortran code here, will it be 64-bit or 32 bit?

When I install applications (like matlab), should I choose 64-bit version or 32-bit version?

Actually I installed 32-bit version matlab and it doesn't work. Matlab itself opted to install 64-bit version. And it worked!

So considering 64bit machines are more expensive than 32-bit ones, we can just get 32-bit ones instead?

What is the catch?

Thanks

---

### Post by Frak on 2009-09-03
If your machine installed with a 64 bit disk, then...


HOORAY, welcome to 64bit land.

Fortran code will be 64-bit, but it is possible to cross compile (though it is messy).

Install the 64bit version of applications.

Finally, 64-bit machines are the only computers on the market with the exception of netbooks. All AMD's (except Semprons) and the Intel Core 2, Core i7, Centrino, et al. is a 64-bit processor.

---

### Post by steveneddy on 2009-09-03
So what kinda processor is in that machine?

---

### Post by lisati on 2009-09-03
> **Frak said:**
> All AMD's (except Semprons) and the Intel Core 2, Core i7, Centrino, et al. is a 64-bit processor.

Don't tell my desktop machine, it has a Sempron CPU (a 3200+ if memory serves correctly) which happily runs 64-bit Ubuntu Studio. It's only a single core, but who cares?

---

### Post by egalvan on 2009-09-03
> **shakeham said:**
> After installation and Ubuntu is working great. 
I installed from the wrong CD-- 
this is a 64-bit CD and this machine is 32-bit.
It amazes me Ubuntu just runs smoothly and doesn't complain about anything

My question, **is this a problem? **Do I need to worry about it?


The only "problem" is that 64bit Ubuntu **WILL NOT** run on 32bit hardware.

The installer will fail as it does a sanity check on the hardware.

Either the CD is mis-marked and is really 32bit,
or the hardware is really 64bit.

---

### Post by shakeham on 2009-09-03
But this is an old machine I've known for years. It ran Windows XP 32-bit. It is a single-core, it is slow......

It is a ......................
**Dell Dimension 5100C for Home (Pentium 4 3GHz)**

could this one be 64-bit?


> **egalvan said:**
> The only "problem" is that 64bit Ubuntu **WILL NOT** run on 32bit hardware.

The installer will fail as it does a sanity check on the hardware.

Either the CD is mis-marked and is really 32bit,
or the hardware is really 64bit.

---

### Post by Frak on 2009-09-03
> **shakeham said:**
> But this is an old machine I've known for years. It ran Windows XP 32-bit. It is a single-core, it is slow......

It is a ......................
**Dell Dimension 5100C for Home (Pentium 4 3GHz)**

could this one be 64-bit?
The later Pentium 4's were 64-bit.

---

### Post by jocko on 2009-09-03
> **shakeham said:**
> But this is an old machine I've known for years. It ran Windows XP 32-bit. It is a single-core, it is slow......

It is a ......................
**Dell Dimension 5100C for Home (Pentium 4 3GHz)**

could this one be 64-bit?
Yes. If you managed to install 64 bit ubuntu, it's definitely a 64 bit processor.
According to wikipedia:
> In 2004, the initial 32-bit [x86]("http://en.wikipedia.org/wiki/X86") [instruction set]("http://en.wikipedia.org/wiki/Instruction_set") of the *Pentium 4* [microprocessors]("http://en.wikipedia.org/wiki/Microprocessor") was extended by the 64-bit [x86-64]("http://en.wikipedia.org/wiki/X86-64") set.
And:
> The following processors implement the Intel 64 architecture:
 
[LIST]
[*]Intel [NetBurst]("http://en.wikipedia.org/wiki/NetBurst") microarchitecture
[LIST]
[*][Intel Xeon]("http://en.wikipedia.org/wiki/Intel_Xeon") (some models since "Nocona")
[*]Intel [Celeron D]("http://en.wikipedia.org/wiki/Celeron_D") (some models since "Prescott")
[*]Intel [Pentium 4]("http://en.wikipedia.org/wiki/Pentium_4") (some models since "Prescott")
[*]Intel [Pentium D]("http://en.wikipedia.org/wiki/Pentium_D")
[*]Intel [Pentium Extreme Edition]("http://en.wikipedia.org/wiki/Pentium_Extreme_Edition")
[/LIST]
 
[/LIST]


---

### Post by todak on 2009-09-03
```
sudo lshw -c cpu
``` will let you know what bit processor you are running. It is listed as **width:**

---

### Post by shakeham on 2009-09-03
> **todak said:**
> ```
sudo lshw -c cpu
``` will let you know what bit processor you are running. It is listed as **width:**

Viola!

$ sudo lshw -c cpu
[sudo] password for bruce: 
  *-cpu                   
       description: CPU
       product: Intel(R) Pentium(R) 4 CPU 3.20GHz
       vendor: Intel Corp.
       physical id: 400
       bus info: cpu@0
       slot: Microprocessor
       size: 3200MHz
       capacity: 4GHz
       width: 64 bits
       clock: 800MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr

So this is a 64bit machine! I'm actually quite confused. For all these years I've only installed 32-bit WindowsXP on this before and I have never thought of it as 64-bit. 

So this one should also install Windows 64-bit and behave like other new workstations/gaming desktops that have touted 64-bit? (of course it is slower)

Thanks guys I've learned sth new

---

### Post by NoaHall on 2009-09-03
Windows sucks on 64 bit - you can't install things like you can on Linux.

I'd only use it if you have more than 4 gb of ram, like I do. Otherwise, I would have stayed 32 bit in windows, 64 bit in linux.

---

### Post by Wiebelhaus on 2009-09-03
> **egalvan said:**
> The only "problem" is that 64bit Ubuntu **WILL NOT** run on 32bit hardware.

The installer will fail as it does a sanity check on the hardware.

Either the CD is mis-marked and is really 32bit,
or the hardware is really 64bit.

I agree , somethings amiss.

---

### Post by jeneverboy on 2009-09-10
Hi

I have a 32-bit ubuntu on a 64-bit machine, should I install (for instance matlab) 32-bit version? And is the 32-bit ubuntu slower than the 64-bit?

Thanks, Alex.

---

### Post by Joshua Lückers on 2009-09-10
> **jeneverboy said:**
> Hi

I have a 32-bit ubuntu on a 64-bit machine, should I install (for instance matlab) 32-bit version? And is the 32-bit ubuntu slower than the 64-bit?

Thanks, Alex.

When running a 32-bit OS you should also install 32-bit software. It might be possible that a 32-bit OS is slower at some parts compared to a 63-bit OS.

---

### Post by solitaire on 2009-09-10
wow!!

I never knew that my Celeron CPU was 64 bit 0_o 
(I'm away to hand in my techie credentials now!!) :(

lol!!
```

  *-cpu                   
       description: CPU
       product: Intel(R) Celeron(R) CPU          550  @ 2.00GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: 6.6.1
       serial: 0001-0661-0000-0000-0000-0000
       slot: U10
       size: 2GHz
       capacity: 2GHz
       width: 64 bits
       clock: 133MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx x86-64 constant_tsc up arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm

```

it's a good excuse to wipe and install 64 bit version later in the week :D lol!!!

---

### Post by miklcct on 2009-09-11
You should definitely install a 64-bit OS in order to boost performance of native applications.

---

### Post by P4man on 2009-09-11
> **solitaire said:**
> wow!!
I never knew that my Celeron CPU was 64 bit 0_o 
(I'm away to hand in my techie credentials now!!) :(


Intel hid the 64 bit capability of their chips for some years as they where quite embarrassed having to implement AMD's instruction set. They had been shouting for years no one needed 64 bit on the desktop and on the server they had Itanium. So when they quietly followed AMD's initiative, they gave it silly names like "EM64T Extended memory techology.."  anything to differentiate it from what their marketing defined as a "real" 64 bit chip (Itanium).

In short: you are forgiven. Its not like it will have been printed in big letters on the box, unlike AMD that called all their chips 64 this and 64 that :)

---

### Post by egalvan on 2009-09-14
> **P4man said:**
> **as they where quite embarrassed **having to implement AMD's instruction set.

:lolflag: and even more embarrassed at having their chips run SO MUCH slower, even at similar clock speeds.
And add on even *more* embarrassment when the dual-cores came out.
In those days, AMD absolutly ate Intel's lunch, and dinner, and breakfast... :lolflag:


 > They had been shouting for years **no one needed 64 bit on the desktop **and on the server they had Itanium. So when they quietly followed AMD's initiative, they gave it silly names like "EM64T Extended Memory Technology.."  anything to differentiate it from what their marketing defined as a "real" 64 bit chip (Itanium).

In short: you are forgiven. Its not like it will have been printed in big letters on the box, unlike AMD that called all their chips 64 this and 64 that :)

They used to shout
[B]no one needs 8-bit...
wait..
no one needs 16-bit...
wait...
no one needs 32-bit
[/B]
and without competition, you can bet they'll be shouting...
[B]no one needs 128 bits
wait...
no one needs 256 bits
wait...
no one needs quantum bits
wait...
no one needs positronic pathways[/B]

And you are correct, AMD always maxed out the 64-bit value of their CPU families.

---

### Post by P4man on 2009-09-14
> **egalvan said:**
> 
They used to shout
[B]no one needs 8-bit...
wait..
no one needs 16-bit...
wait...
no one needs 32-bit
[/B]

Thats nonsense. Their first chip was 8 bit, their 16 and especially 32 bit architectures were on the market well before there was any real need for their capabilities (in memory addressing). Remember the 386? It came out in 1985, there wasn't even a 32 bit consumer OS on the horizon. We still ran DOS with less than 1Mb Ram. Windows 3.1 came out 7 years later and barely used any of the 386 capabilities. It wasn't until windows 95, ten years later where the ISA was really leveraged and people commonly used >4Mb RAM, used protected mode and all the other goodies i386 introduced.

Back then, intel (rightly) argued they needed to seed the market with hardware early so software developers could catch up and start building 32 bit software without having to worry much about any users still using 16 bit cpu's.  When win95 came out, no one would expect it to run on 286 class machine. The cpu's with the needed capabilities (i386 and up) where being sold for 10 years.

32->64 bit was vastly different. People were hitting brick walls, especially in servers, but arguably on the desktop as well.  But the 64 bit cpu's came so late, for the next 5 years at least software developers, OS's makers, driver developers will have to take 32 bit in to account.

---

### Post by egalvan on 2009-09-14
> **P4man said:**
> Thats nonsense. Their first chip was 8 bit, their 16 and especially 32 bit architectures were on the market well before there was any real need for their capabilities (in memory addressing). Remember the 386? It came out in 1985, there wasn't even a 32 bit consumer OS on the horizon. We still ran DOS with less than 1Mb Ram. Windows 3.1 came out 7 years later and barely used any of the 386 capabilities. It wasn't until windows 95, ten years later where the ISA was really leveraged and people commonly used >4Mb RAM, used protected mode and all the other goodies i386 introduced.

Nonsense :) yeah... :lolflag:

Do I remember the 386?
Yeah, I remember the 80386.
Heck, I remember the 80286, the 80186, the 8086...
and more importantly, I remember the **4004**

"What's that?" you ask? :)

Well, let me tell you...

it was a 4-bit CPU. yes, four bit. All four. No more.

Just because Intel or Microsoft didn't make them, doesn't mean they didn't exist.
We ran OTM (Other than Microsoft) such as CP/M, DR-DOS, and others which escape me (old age, cough cough),
 and all of them were superior to anything Gates had.

We built (with soldering iron in hand) and ran machines from the likes of SWTCC and MITS, et al.
Remember those?
The Steves hadn't made much noise up to that time.

Motorola, Zilog, DEC and TI were also in the game, among others.
and most of them were superior to anything Intel had. 
(most had much better memory management/mapping than the *kludge* from Intel.
 Motorola was especially elegant, ah the beauty of it still brings a tear to my eye... sniff)

Yeah, I go back further than you think, young man. :)
Back then, we had to program our computers up-hill, both ways,
in the snow and searing, blinding sun. A man was a man, let me tell you :lolflag:
(hand-optimized machine language, assembler and FORTRAN. Yes, we actually did this)

( And as an aside, for the first few years, I saw only one female programmer. It's not that we didn't like them, or that we didn't want them around (heck, most of us had Lady Lovelace as a pin-up)...
It's just that they were scarcer than hen's teeth in those days. )

> Back then, intel (rightly) argued they needed to seed the market with hardware early **so software developers could catch up** and start building 32 bit software without having to worry much about any users still using 16 bit cpu's. ** When win95 came out, no one would expect it to run on 286 class machine. **The cpu's with the needed capabilities (i386 and up) where being sold for 10 years.

Again, Microsoft and Intel were not the only games, in town. :)
There were many using software systems that were crying out for better memory management, register utilization, etc.

Windows 98 could not run on anything less than a 80386 because it was written to utilize a specific memory-manage function of that class of Intel hardware.
The 80286 had it, but it was poorly implemented.
it could have run on Motorola's offerings due to better memory management. ( one wonders how much better it would have run ?? )

Microsoft's implementation of high memory usage was not very well liked by most programmers in the day...
There was another company that had a much-superior method, along with good hardware support from the RAM industry.
Expanded Memory versus Extended Memory. 
Expanded was more elegant, more extensible.
We ended up with Extended, a Win-Tel thing.
We ran a multi-tasker that was FAR superior to the pathetic "program switcher" MS had, especially when run under Expanded RAM software/hardware, with a good OS.

> 32->64 bit was vastly different. People were hitting brick walls, especially in servers, but arguably on the desktop as well.  But the 64 bit cpu's came so late, for the next 5 years at least software developers, OS's makers, driver developers will have to take 32 bit in to account.


Yeah, the Win-Tel steam-roller conglomerate eventually squashed almost everything in it's path.

Apart from Apple, there was one other computer that had a very stable system, with full color and stereo sound long before Win-Tel did.

**But**...
I go back to 1969 in reference to computer stuff.
My dad goes back to 1963, when he helped debug OS's for (I believe) a fledging company eventually called Digital Equipment Corporation.
He also did theoretical work for Burroughs and Sperry-UniVAC.

**So**...
A lot of what I wrote about "no one needs" is more **tongue-in-cheek **than  position-paper monograph...
It was meant to be light-hearted.

because, let's face it, almost no home or office users *need* the ridiculously fast and memory-laden machines to surf the Internet, chat, and write term papers.

But since when has "need" dictated our "wants" ? ? :lolflag:

And in closing,

remember that Bill Gates once tried to convince us that no one would ever need more than 512K of RAM.

:popcorn:

---

### Post by P4man on 2009-09-14
I wrongly assumed you where a young man, but that doesn't mean you have to make the same wrong assumption :p

Im aware of what you write, but I stand by my point that 16 and 32 bit capabilities where released (by intel) to the market long before there was any significant demand or need in the markets where intel competed. This is in stark contrast to the their long overdue 64 bit extension of x86.
> 
remember that Bill Gates once tried to convince us that no one would ever need more than 512K of RAM.

640k, at least that is the popular myth, but is dubious if he ever actually said it. FWIW, he denies it:

> Ive said some stupid things and some wrong things, but not that. No one involved in computers would ever say that a certain amount of memory is enough [...] But even 32 bits of address space won't prove adequate as times goes on [...] Meanwhile, I keep bumping into that silly quotation attributed to me that says 640 k of memory is enough. 

Thats enough off topic blabbering from me :)

---

### Post by 3rdalbum on 2009-09-14
> **P4man said:**
> 640k, at least that is the popular myth, but is dubious if he ever actually said it. FWIW, he denies it:

[...]But even 32 bits of address space won't prove adequate as times goes on [...]

He should know, he started the Windows Vista project :-P

I must admit, I never realised that my old Sempron processor was 64-bit until I tried using the 64-bit CD, just to see what would happen. My post about it was somewhat like yours... I asked "Can a 32-bit machine run the 64-bit CD, or is my CPU actually 64-bit?".

---

### Post by StuartN on 2009-09-14
Is there any disadvantage to running 64-bit Ubuntu? I have some treasured, no-longer maintained applications (like e.g. Notecase) - will they still run under 64-bit Ubuntu?

Like the OP, I had no idea my AMD Semprom Mobile was 64-bit, and wonder if I should be putting the 64-bit version on the next time I upgrade my operating system (but have no intention of messing with a perfectly adequate install until then).

---

### Post by NoaHall on 2009-09-14
No, they won't have any problems, as anything that isn't 64 bit, can just be forced. Most apps have 64 bit version these days, or you can compile them yourself if they aren't.

---

### Post by P4man on 2009-09-14
> **StuartN said:**
> Is there any disadvantage to running 64-bit Ubuntu? I have some treasured, no-longer maintained applications (like e.g. Notecase) - will they still run under 64-bit Ubuntu?

Like the OP, I had no idea my AMD Semprom Mobile was 64-bit, and wonder if I should be putting the 64-bit version on the next time I upgrade my operating system (but have no intention of messing with a perfectly adequate install until then).

Im gonna make a strange analogy: its a bit like with recycling: there is no real obvious advantage to an individual doing it, but if everyone does it, it does benefit everyone (like cleaner environment).

Its similar with 64 bit. Unless you are stretching the addressing limitations of 32 bit (>~3GB Ram), or doing certain very specific tasks like video encoding, there is no real benefit. But it would make life easier for developers if people would start standardizing on 64 bit hard and software sooner rather than later. Id suggest you try the 64 bit version on your next install, but its not likely you'll see any benefit from upgrading.

---

### Post by Irvine_himself on 2009-09-14
> **egalvan said:**
> :lolflag: 
They used to shout
[B]no one needs 8-bit...
wait..
no one needs 16-bit...
wait...
no one needs 32-bit
[/B]


I have a friend with various business interests, modern desktops and servers etc but he is still running a couple of his original old BBC Acorn's with the 6502 chip, 16 KB of user memory, (which was later jiggery pokeried into 32 KB.

One holds his original dial up "Bulletin Board" which, as of the last time I checked, was still working, connected and, he claims, still has users????

The other once a month still prints out a database of mailing address labels. He say's that he is to lazy to actually change everything over into a modern format, but I suspect that it is pure nostalgia.

I hope this bring tears of pleasure to oldies of the world.

---

### Post by sopadeajo on 2009-09-14
"remember that Bill Gates once tried to convince us that no one would ever need more than 512K of RAM."

Didn't he try to convince you that ms-dos (or later windows) would ever be the OS you'll need?

Of the two enormous lies, last one is still worse.

---

