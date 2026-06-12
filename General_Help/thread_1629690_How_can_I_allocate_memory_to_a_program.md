---
title: "How can I allocate memory to a program?"
date: 2010-11-24
forum: General Help
---

### Post by mindlessbrain on 2010-11-24
Hello,

I am running BWA (burrow-wheeler alignment) and, keep getting an error that there isn't enough memory allocated. How do I change the memory allocation? I'm working on a good quality desktop only a little over a year old, so having the memory shouldn't be the problem. 

Thanks in advance!

mb

---

### Post by sikander3786 on 2010-11-24
How much memory is there? And how much do you think BWA needs?

While BWA is running, please post the output of

```
free
```

---

### Post by mindlessbrain on 2010-11-24
```

root@jill-desktop:/home/jill# bwa index -a bwtsw /home/jill/bwa-0.5.8c/Run/homotaysachs.fasta
[bwa_index] Pack FASTA... 0.00 sec
[bwa_index] Reverse the packed sequence... 0.00 sec
[bwa_index] Construct BWT for the packed sequence...
BWTIncConstruct() : Not enough memory allocated!

```

I believe BWA needs 2.5G.

---

### Post by mindlessbrain on 2010-11-24
bump.

---

### Post by endotherm on 2010-11-24
this is not something an operator can control, only a developer. My guess is it's actually stack size that is to big, rather than allocated heap, but your error is in a constructor so who knows. 

what is your 'free' output while the program is running?

---

### Post by jocko on 2010-11-24
@mindlessbrain: Do you run 64 bit or 32 bit ubuntu?
I don't think 32 bit can allocate more than 2 Gb ram to a single application (I may be wrong).

---

### Post by mindlessbrain on 2010-11-25
> **endotherm said:**
> this is not something an operator can control, only a developer. My guess is it's actually stack size that is to big, rather than allocated heap, but your error is in a constructor so who knows. 

what is your 'free' output while the program is running?

What do you mean by free output?

---

### Post by jocko on 2010-11-25
> **mindlessbrain said:**
> What do you mean by free output?
Type "free -m" in a terminal. It shows your memory usage.

---

### Post by mindlessbrain on 2010-11-26
```

jill@jill-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3276        713       2563          0         98        319
-/+ buffers/cache:        295       2980
Swap:         9597          0       9597

```

---

### Post by conradin on 2010-11-26
[http://linux-software-news-tutorials.blogspot.com/2010/10/control-amount-of-ram-used-by-ubuntu.html](http://linux-software-news-tutorials.blogspot.com/2010/10/control-amount-of-ram-used-by-ubuntu.html)

the link above is about controlling swap space. I'm interested in seeing a few lines of output to the code vmstat 1 100 during this BWA programs runtime.

---

### Post by endotherm on 2010-11-27
based on your free, the problem is definitely not that you are out of memory, or that you have hit some kind of limit. was bwa running when you ran free -m?

I see that you feed your program an input file. if the program is only expecting a certain amount of data, and you provide more, you could end up with memory errors. have you made any tweaks to it? is it possible to try with a newly downloaded copy?

---

### Post by jocko on 2010-11-27
> **endotherm said:**
> based on your free, the problem is definitely not that you are out of memory, or that you have hit some kind of limit. was bwa running when you ran free -m?

I see that you feed your program an input file. if the program is only expecting a certain amount of data, and you provide more, you could end up with memory errors. have you made any tweaks to it? is it possible to try with a newly downloaded copy?
From bwa's m[anual on the developer's sourceforge]("http://bio-bwa.sourceforge.net/bwa.shtml#8") page:> 
      **    Memory Requirement**

     With bwtsw algorithm, 2.5GB memory is required for indexing the complete human genome sequences. For short reads, the  **&#8216;aln&#8217;** command uses ~2.3GB memory and the  **&#8216;sampe&#8217;** command uses ~3.5GB. 
From mindlessbrain's command and the name of the input file in post #3 it looks very much like she/he is trying to index a human genome. I'm pretty sure that the amount of data (both number and length of individual reads) from a whole-genome sequence can vary pretty much depending on the technology used and other factors in the set-up of the sequencing run, so it's probably possible that 2.5GB is enough in some cases but not others (you'll probably need to read the developer's [FAQ]("http://bio-bwa.sourceforge.net/") and published papers to see if this is true or not).

But it would be weird if mindlessbrain's total amount of memory (3.2 Gb RAM + ~9.4 Gb swap) is not enough, which makes me suspect that the problem is that she/he is trying to do this in a 32 bit operating system, which probably can't allocate enough memory to a single process.

**@Mindlessbrain:** I ask again: Do you try to run this in a 32bit or 64 bit operating system? If you're not sure, post the output you get from these commands:
```
uname -m
cat /proc/cpuinfo
```The first will say "x86_64" if you have a 64 bit os, and "i686" (or possibly "i386", not sure) for a 32 bit os. The second command will tell us what cpu you have, so we can see if you have a 64 bit cpu.

And another thing: Was the free output taken while the command was still running or after it had already quit? If the program was not running and actually using memory it is impossible to know how much memory it was using before it quit...

---

### Post by mindlessbrain on 2010-11-27
jill@jill-desktop:~$ uname -m
i686
jill@jill-desktop:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 6
model name    : AMD Athlon(tm) II X2 245 Processor
stepping    : 2
cpu MHz        : 800.000
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips    : 5824.26
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 6
model name    : AMD Athlon(tm) II X2 245 Processor
stepping    : 2
cpu MHz        : 800.000
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips    : 5811.04
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

So it looks like I am running a 32 bit. 

I have to allow bwa to index my files before aligning them. I'm not trying to align an entire genome, just a translated mRNA. So a rather small portion of the human genome. This is just a get it running file I use with most of my bioinformatics tools. 

When I try it with a different file it seems like I get slightly farther along.

bwa index -a bwtsw /home/jill/bwa-0.5.8c/Run/disease.txt

I also tried the swappy thing, no go. 

I'm going to try from a clean install, and report back.

---

