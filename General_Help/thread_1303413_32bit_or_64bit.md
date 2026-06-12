---
title: "32bit or 64bit"
date: 2009-10-28
forum: General Help
---

### Post by Psycho.mario on 2009-10-28
How can i find out if my processor is 64bit? I can't find any commands on the internet that tell me outright

Thanks

---

### Post by howefield on 2009-10-28
Do you know what processor you have ?

Or maybe the make/model of the machine ?

Or if you try loading a 64 bit Live cd, it will fail unless your machine can support it.

---

### Post by wojox on 2009-10-28
```
uname -m
```

For Linux, it will return i386 or i686 for 32-bit processors or x86_64 for 64-bit ones.

---

### Post by Psycho.mario on 2009-10-28
uname -m shows the kernel, not the processor. I have a dell inspiron 530

cat /proc/cpuinfo:
```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 22
model name    : Intel(R) Celeron(R) CPU          420  @ 1.60GHz
stepping    : 1
cpu MHz        : 1596.114
cache size    : 512 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx lm constant_tsc up arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips    : 3192.22
clflush size    : 64
power management:

```

---

### Post by XCan on 2009-10-28
Looks like it does: [http://ark.intel.com/Product.aspx?id=29734&processor=420&spec-codes=SL9XP](http://ark.intel.com/Product.aspx?id=29734&processor=420&spec-codes=SL9XP)

---

### Post by masux594 on 2009-10-28
.. your cpu is x64..

Sysc, A

---

### Post by Psycho.mario on 2009-10-28
Thank you. Now, i know the following question has been asked a million times, but for my hardware: is it worth swapping over to 64bit ubuntu? (I don't need the extra RAM addressing because i only have 3gb)

---

### Post by Anthon on 2009-10-28
For me running into trouble with VLC (VideoLan) and Skype meant I went back to 32 bit for my desktop machine (IIRC the issues were sound-related). For a server I have I decided to stick with 64 bit, but there is no desktop on that.
Question is do you think it is worth the risk and time of reinstalling 32bit if 64bit doesn't work out for you.

---

### Post by SuperSonic4 on 2009-10-28
> **Psycho.mario said:**
> Thank you. Now, i know the following question has been asked a million times, but for my hardware: is it worth swapping over to 64bit ubuntu? (I don't need the extra RAM addressing because i only have 3gb)

Why not switch? Flash works, Java works, codecs work. I don't use Skype or Google Earth so I can't comment. Amazon's downloader is 32 bit but you can install 32bit libs if needed.

Besides, you may want to upgrade your ram in the future ;)

---

### Post by philinux on 2009-10-28
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

From the 64 bit forum.

However, I've been using 64 bit for 18 months now with no problems at all.

---

### Post by howefield on 2009-10-28
> **Psycho.mario said:**
> Thank you. Now, i know the following question has been asked a million times, but for my hardware: is it worth swapping over to 64bit ubuntu? (I don't need the extra RAM addressing because i only have 3gb)

Have a wander through the 64bit forum here, get a feel for what people are saying, what the problems are, ect. There are plenty of threads asking the same question.

[http://ubuntuforums.org/forumdisplay.php?f=343](http://ubuntuforums.org/forumdisplay.php?f=343)

My experience has been excellent with 64 bit, and my view is that if your hardware supports it, there is no reason not to.

---

### Post by 3rdalbum on 2009-10-28
I never even had a 32-bit Jaunty CD, so my father uses 64-bit without complaints and so does my mate. (who wouldn't understand "64-bit" if I tried to explain it to him).

---

### Post by Psycho.mario on 2009-10-28
I might try it tomorrow, with the new release. I'm always re-installing so there are no worries about losing important data, i don't have any. Thanks for the input, it's helped a lot.

---

