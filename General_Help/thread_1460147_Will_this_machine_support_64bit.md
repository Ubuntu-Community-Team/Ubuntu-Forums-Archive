---
title: "Will this machine support 64bit?"
date: 2010-04-22
forum: General Help
---

### Post by DougieFresh4U on 2010-04-22
I know it looks like a silly question, but I need to know.
Some one gave me this machine yesterday and I would like to run 64bit.
It's an:
[B]AMD Sempron 3200+
120 GB hard drive
1.5 GB RAM[/B]
Is there a 'code' for terminal to tell me?
Thanks

---

### Post by muteXe on 2010-04-22
"sudo cat /proc/cpuinfo"


I think!  If you see "lm" in the flags, then yes it can.

---

### Post by maxrpowell on 2010-04-22
maybe there is something useful here??
[http://ubuntuforums.org/showthread.php?t=1116366](http://ubuntuforums.org/showthread.php?t=1116366)
sorry if it doesn't work

---

### Post by DougieFresh4U on 2010-04-22
Well this is what I got from 'code' provided:
```
rocessor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 47
model name	: AMD Sempron(tm) Processor 3200+
stepping	: 0
cpu MHz		: 1800.000
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm
bogomips	: 3582.18
clflush size	: 64
power management: ts fid vid ttp tm stc
```

So I guess not?
Thanks for replies.

---

### Post by muteXe on 2010-04-22
Doesnt look like it can.
The best test of course is to just try the live 64 bit CD.  It wont boot if you aint got a 64bit architecture.

---

### Post by DougieFresh4U on 2010-04-22
It's only 32bit
Thanks every one. :)

---

### Post by oldos2er on 2010-04-22
> **DougieFresh4U said:**
> 
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt [COLOR="Red"]lm[/COLOR] 3dnowext 3dnow up pni lahf_lm


The 'lm' flag indicates a 64-bit capable processor.

Btw, no need to use sudo with cat.

---

### Post by muteXe on 2010-04-22
Blimey I'm going blind. I didn't see "lm" in there.

---

### Post by RTrev on 2010-04-22
Well, this says it *is* 64-bit:

[http://www.geeks.com/details.asp?invtid=SDA3200CNBOX-DT&cat=CPU](http://www.geeks.com/details.asp?invtid=SDA3200CNBOX-DT&cat=CPU)

<g>

---

### Post by DougieFresh4U on 2010-04-22
> **oldos2er said:**
> The 'lm' flag indicates a 64-bit capable processor.

Btw, no need to use sudo with cat.

> **RTrev said:**
> Well, this says it *is* 64-bit:

[http://www.geeks.com/details.asp?invtid=SDA3200CNBOX-DT&cat=CPU](http://www.geeks.com/details.asp?invtid=SDA3200CNBOX-DT&cat=CPU)

<g>

Thanks.
I am gonna try 64bit cd in a few minutes

---

### Post by DougieFresh4U on 2010-04-23
Yes, 64bit is working on this AMD Sempron 3200+
Thanks for all the replies as they helped, but the true test was installing and I must say what a very fast boot up I got and although my graphics is an onboard ATI Radeon Xpress 200, it seems to be working great, compiz is working and I can set 'visual effects' to the 'Extra' setting with no 'drama.

---

