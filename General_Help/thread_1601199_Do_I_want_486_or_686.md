---
title: "Do I want 486 or 686?"
date: 2010-10-19
forum: General Help
---

### Post by princerameses on 2010-10-19
I'm not sure which one to download. [Download page here]("http://mirror.cs.vt.edu/pub/MEPIS/antix/")

Do I want 486 or 686? I have an older compaq pesario. I think it's from 2002.

Thanks.

---

### Post by Quadunit404 on 2010-10-19
They both basically mean the same thing: 32-bit OS.

---

### Post by kerry_s on 2010-10-19
> **princerameses said:**
> I'm not sure which one to download. [Download page here]("http://mirror.cs.vt.edu/pub/MEPIS/antix/")

Do I want 486 or 686? I have an older compaq pesario. I think it's from 2002.

Thanks.

you want 686.

---

### Post by RJARRRPCGP on 2010-10-19
> **princerameses said:**
>  i think it's from 2002.



686.

---

### Post by princerameses on 2010-10-19
Thanks. :)

---

### Post by efflandt on 2010-10-19
486 would be for a really old 486 or possibly a 386DX if it has a separate 387 math co-processor chip.

Early plain Pentiums and Celerons are technically 586, but can run 486 code.  I think AMD K6-2/400 were also in 586 class.  I have an old Celeron 300 server in my basement running what it says is an i586 kernel in SuSE 8.2 (old).

686 would be 32-bit for Pentium Pro or Pentium II or newer.

I found many forum posts, but not much authoritative, in a quick web search, so I am basing this on experience and what it says farther down on [http://www.nasm.us/doc/nasmdoc6.html](http://www.nasm.us/doc/nasmdoc6.html)

I first ran Linux on a 386DX33, later hot rodded with Cyrix 486DRx2/66 and 387 math co-processor.

---

### Post by anticapitalista on 2010-10-20
The 486 is for AMD k5/k6 and PI CPUs.

---

### Post by utilitytrack on 2010-10-20
> **efflandt said:**
> 486 would be for a really old 486 or possibly a 386DX if it has a separate 387 math co-processor chip.

Early plain Pentiums and Celerons are technically 586, but can run 486 code.  I think AMD K6-2/400 were also in 586 class.  I have an old Celeron 300 server in my basement running what it says is an i586 kernel in SuSE 8.2 (old).

686 would be 32-bit for Pentium Pro or Pentium II or newer.

I found many forum posts, but not much authoritative, in a quick web search, so I am basing this on experience and what it says farther down on [http://www.nasm.us/doc/nasmdoc6.html](http://www.nasm.us/doc/nasmdoc6.html)

I first ran Linux on a 386DX33, later hot rodded with Cyrix 486DRx2/66 and 387 math co-processor.

It's great answer. Well done, **efflandt**.

---

### Post by P4man on 2010-10-20
I dont understand why they still maintain a 486 version when the OS can realistically never be run on one. Their own minimum specs say Pentium II with 64 MB (if preconfigured swap) or 128Mb, When was the last time you saw a 486 or even pentium with that much ram? A 486 would typically have 4 to 8  MB ram. A late pentium maybe 16 or 32.

---

### Post by psusi on 2010-10-20
> **P4man said:**
> I dont understand why they still maintain a 486 version when the OS can realistically never be run on one. Their own minimum specs say Pentium II with 64 MB (if preconfigured swap) or 128Mb, When was the last time you saw a 486 or even pentium with that much ram? A 486 would typically have 4 to 8  MB ram. A late pentium maybe 16 or 32.

My best friend in high school and a dual pentium 100 MHz with 128 mb of ram ;)

Of course that was when I had a 90 MHz Pentium with 16 mb of ram and a "massive" 1 gb hd that I thought I would never fill up.

---

### Post by anticapitalista on 2010-10-20
> **P4man said:**
> I dont understand why they still maintain a 486 version when the OS can realistically never be run on one. Their own minimum specs say Pentium II with 64 MB (if preconfigured swap) or 128Mb, When was the last time you saw a 486 or even pentium with that much ram? A 486 would typically have 4 to 8  MB ram. A late pentium maybe 16 or 32.

Read post 2 above yours. ie 
The 486 is for AMD k5/k6 and PI CPUs.

---

### Post by psusi on 2010-10-20
> **anticapitalista said:**
> Read post 2 above yours. ie 
The 486 is for AMD k5/k6 and PI CPUs.

Read the post you quoted ;)

Those cpus are below the minimum requirements.

---

### Post by cascade9 on 2010-10-20
> **efflandt said:**
> 486 would be for a really old 486 or possibly a 386DX if it has a separate 387 math co-processor chip.

Early plain Pentiums and Celerons are technically 586, but can run 486 code.  I think AMD K6-2/400 were also in 586 class.  I have an old Celeron 300 server in my basement running what it says is an i586 kernel in SuSE 8.2 (old).

686 would be 32-bit for Pentium Pro or Pentium II or newer.

I found many forum posts, but not much authoritative, in a quick web search, so I am basing this on experience and what it says farther down on [http://www.nasm.us/doc/nasmdoc6.html](http://www.nasm.us/doc/nasmdoc6.html)

I first ran Linux on a 386DX33, later hot rodded with Cyrix 486DRx2/66 and 387 math co-processor.

Difficult to say exactly what is what in some ways (i686 was pretty much just an intel designation). One minor correction- Celerons were all based on the P6 (Pentium Pro) or later architectures, so they are i686 (or later). 

AFAIK, you can run i686 code on earlier CPUs, just there is a chance that something will go wrong. The futher away you get, the more likely that will happen (i686 code on a i586, should probably fine. On a i386, far greater chance of something going badly wrong)

> **anticapitalista said:**
> Read post 2 above yours. ie 
The 486 is for AMD k5/k6 and PI CPUs.

*sigh* No.

Pentium is i586. 

> The name Pentium was derived from the [Greek]("http://en.wikipedia.org/wiki/Greek_language") *pente* (&#960;&#941;&#957;&#964;&#949;), meaning 'five', and the [Latin]("http://en.wikipedia.org/wiki/Latin") ending *[-ium]("http://en.wikipedia.org/wiki/Latin_declension#Third_declension_i-stem_nouns")*, a name selected after [courts had disallowed]("http://en.wikipedia.org/wiki/Pentium_%28brand%29#Origins_of_Pentium_trademark") trademarking of number-based names like "i586" or "80586"

[http://en.wikipedia.org/wiki/Pentium](http://en.wikipedia.org/wiki/Pentium)

K5 should be i586 (K5s run all of the instructions of the P5).

---

### Post by utilitytrack on 2010-10-21
> **cascade9 said:**
> One minor correction- Celerons were all based on the P6 (Pentium Pro) or later architectures, so they are i686.

Yes, you are right. Thanks for pointing on this.
> [I]The Intel Celeron processor is based on the P6 microarchitecture and is optimized for the Value PC market segment. The Intel Celeron processor, like the Pentium® II processor, features a Dynamic Execution microarchitecture and executes MMX&#8482; technology instructions for enhanced media and communication performance.

**Intel(R) Celeron(R) Processor Datasheet, [http://www.intel.com/design/celeron/datashts/243658.htm]("http://www.intel.com/design/celeron/datashts/243658.htm")**[/I]

---

### Post by P4man on 2010-10-21
Regardless, its still weird they support a kernel specifically for CPU's that predate pentium pro/K6/celeron, so only for 488, Pentium classic/MMXs and AMD K5s when the OS needs more RAM than 98% of those will have. 

Maybe its for some specific device, I remember not so long reading about a 486 compatible (not intel, amd or via, but something else) CPU used in a a "commodore 64 style" keyboard-PC. Was it a Rise cpu? Not sure, iirc it was running ~266 Mhz.

---

### Post by cascade9 on 2010-10-21
@ P4man- The K6s (all models) are i586 as well, and there are more than a few VIA C3 (ex-cyrix) chips that are i586 as well. IIRC, the Samuel 2, Ezra and Ezra-T chips are i586, Nehemiah is i686.  

> **utilitytrack said:**
> Yes, you are right. Thanks for pointing on this.

LOL, no problem. Funny that intel managed to make a P6 core that slow... but when you remove ALL the cache from the CPU thats what happens. Those original celerons were much, much much slower than the MHz would make you think, the 266 and cacheless 300MHz celerons make P1 200s look fast!

---

### Post by anticapitalista on 2010-10-21
> **psusi said:**
> Read the post you quoted ;)

Those cpus are below the minimum requirements.

To clear up a misunderstanding.
The OP asked which version of antiX to use on his/her box. The 486 version of antiX is for k5/k6 and PI boxes and the 686 version is for others. There is no 586 version of antiX.

---

