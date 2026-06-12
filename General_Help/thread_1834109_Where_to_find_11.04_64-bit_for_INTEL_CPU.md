---
title: "Where to find 11.04 64-bit for INTEL CPU ?"
date: 2011-08-27
forum: General Help
---

### Post by primorec on 2011-08-27
[FONT="Courier New"]I just bought new Lenovo ThinkPad T520 laptop. It came preinstalled with WINDOWS 7  64-bit Home Premium Edition. So, I am pretty convinced that this IS 64-bit laptop. So far so good.  
Here my problems start. I want to install LINUX on this laptop. To be specific, I want to install Ubuntu 11.04 64-bit Operating System. After more than hour searching the net I was able to find Ubuntu 11.04 AMD64, I COULD NOT find 64-bit version of ubuntu for the INTEL CPU. I was able to find ONLY 32-bit version.
So, **[SIZE="3"]I downloaded the 64-bit AMD64 version of the ISO image[/SIZE]**, burned it on CD and try it as a LIVE CD.  The Ubuntu 11.04 AMD64 DOES RUN on INTEL CPU. Later on, I want to install it on the hard disk.  I have a gut feeling that something is not right.

So, my question is:  Where I can download the 64-bit version of the 11.04 for the INTEL CPU from ?

The 'cat /proc/cpuinfo' gives:
ubuntu@ubuntu:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 42
model name	: Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
stepping	: 7
cpu MHz		: 800.000
cache size	: 3072 KB

etc etc etc

address sizes	: 36 bits physical, 48 bits virtual


from [http://ark.intel.com/products/52229/Intel-Core-i5-2520M-Processor-%283M-Cache-2_50-GHz%29](http://ark.intel.com/products/52229/Intel-Core-i5-2520M-Processor-%283M-Cache-2_50-GHz%29)

Status        Launched
Launch Date	Q1'11
Processor Number  	i5-2520M
# of Cores 2
# of Threads 4
Clock Speed 2.5 GHz
Max Turbo Frequency 3.2 GHz
Intel® Smart Cache 3 MB
Bus/Core Ratio 25
DMI 5 GT/s
**[SIZE="3"]Instruction Set  64-bit[/SIZE]**
Instruction Set Extensions  AVX[/FONT]

---

### Post by dcstar on 2011-08-27
> **primorec said:**
> [FONT="Courier New"]I just bought new Lenovo ThinkPad T520 laptop. It came preinstalled with WINDOWS 7  64-bit Home Premium Edition. So, I am pretty convinced that this IS 64-bit laptop. So far so good.  
Here my problems start. I want to install LINUX on this laptop. To be specific, I want to install Ubuntu 11.04 64-bit Operating System. After more than hour searching the net I was able to find Ubuntu 11.04 AMD64, I COULD NOT find 64-bit version of ubuntu for the INTEL CPU. I was able to find ONLY 32-bit version.
So, I downloaded the 64-bit AMD64 version of the ISO image, burned it on CD and try it as a LIVE CD.  The Ubuntu 11.04 AMD64 DOES RUN on INTEL CPU. Later on, I want to install it on the hard disk.  I have a gut feeling that something is not right.

So, my question is:  Where I can download the 64-bit version of the 11.04 for the INTEL CPU from ?


There is no such thing, Intel CPUs use the same 64-bit distro, your "gut feeling" is totally bogus.

---

### Post by primorec on 2011-08-27
> **dcstar said:**
> There is no such thing, Intel CPUs use the same 64-bit distro, your "gut feeling" is totally bogus.

[FONT="Courier New"]Thanks.  I do agree with your comment regarding "bogusness".

If I understand your answer correctly, the users who would like to install 64-bit version of the ubuntu 11.04 on 64-bit INTEL based motherboard need to select 64-bit version of the distro marked **[SIZE="3"]AMD64.[/SIZE]**

Pretty clever,   isn't ?[/FONT]

---

### Post by dcstar on 2011-08-27
> **primorec said:**
> [FONT="Courier New"]Thanks.  I do agree with your comment regarding "bogusness".

If I understand your answer correctly, the users who would like to install 64-bit version of the ubuntu 11.04 on 64-bit INTEL based motherboard need to select 64-bit version of the distro marked **[SIZE="3"]AMD64.[/SIZE]**

Pretty clever,   isn't ?[/FONT]

[LIST=1]
[*]Please stop using fancy fonts, it is annoying and against forum policies.
[*]AMD invented the 64-bit command set, so they get to name it in the same way Intel named the X86 command set.
[/LIST]

---

### Post by primorec on 2011-08-27
> **dcstar said:**
> [LIST=1]
[*]Please stop using fancy fonts, it is annoying and against forum policies.
[*]AMD invented the 64-bit command set, so they get to name it in the same way Intel named the X86 command set.
[/LIST]

I do not think that 'Courier New' is a fancy font. It is pretty much standard for most of programmers.  It keeps the source code easier to read and format on almost any terminal.

Regarding AMD and invention of the 64 bit command set.
Thanks for this info.  I did not know this. All I know is that AMD was chasing INTEL's instruction set evolution on X86 platform all their childhood and adulthood.  It seems that the roles are now reversed.

---

### Post by 3rdalbum on 2011-08-27
I'll agree it's a bit confusing, and you're certainly not the first person to ask the question. However, just as an explorer gets the right to name the place they discover, AMD had the right to name its instruction set.

There's always debates about whether to rename the ISO to reduce the confusion, but it's never really come to anything.

---

