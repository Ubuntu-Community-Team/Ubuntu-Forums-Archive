---
title: "Is my CPU working correctly?"
date: 2011-09-13
forum: General Help
---

### Post by A Traveller on 2011-09-13
Hi All.

I have been asking about my problem and searching for some information on the Internet, but have come across conflicting information. Some people say that it isn't a problem and everything is normal but some people also think that it is a problem and needs rectifying, so I am posting here in the hope that someone who is knowledgeable and experienced in this matter can help.

The pc is using a GA-890GPA-UD3H motherboard with an AMD Phenom II x6 1100T CPU. The motherboard is still on it's original BIOS version and has not been updated to the one which the Gigabyte website indicates that supports this particular CPU.

If I run cat /proc/cpuinfo, each of the 6 cores shows the CPU MHz as being 800MHz. I went to youtube and played an HD 1080p video and then ran the same command as previously. Whenever I did that just one of the cores shows 3300.000 (CPU MHz) and the other five still show 800. Yesterday core no. 4 showed 3300.000 and today it was core no. 0 that showed it.

When customising the menu bar in Ubuntu, I found an icon for the CPU Frequency Scaling Monitor, which I placed on the menu bar. There are 4 speeds and 4 settings (800, 1.7, 2.5, 3.3 MHz and Conservative, Ondemand, Performance, Powersave). It is set to Ondemand by default and with this setting, the speed that displays on the menu bar shows 800, but whenever I do something such as open a program, even a simple text editor or the calculator, it briefly shows 3.3GHz and then goes back to 800MHz. It also keeps going to 3.3.GHz briefly even when nothing is being done.

I have read about Cool n Quiet and the ability of the CPU to remain at low speed when idle and ramp up to higher speeds when required, however, is there anything that doesn't seem quite right in my problem description?

I have also seen lots of suggestions to put the CPU under great stress or use CPU 'burn' software, however, I do not wish to do anything that is unsafe or that I am not knowledgeable about, so is there a simple, SAFE, quick way of testing if my CPU and all the cores are functioning correctly? Note that I do not overclock at all and am not interested in doing so.

Sorry for the very long post but I wanted to explain as much as I could due to seeing different people say different things on the web.

Any advice would be very appreciated.

Thanks.

---

### Post by zero2xiii on 2011-09-13
Hay,

I would say you can rest easy.

I have CPU scaling set to "On demand" on all 4 of my computer, and the same sort of thing happens. Only when I put it on "Performance" when I edit video or render video or such, does it STAY at the highest freq.

Windows does a similar thing, you just don't see it. But I suggest leaving it on "On demand" as it minimizes power consumtion, and heat generation (my CPU runs about 10 deggrees C cooler when it is on 'on demand')

Cherz

---

### Post by Slim Odds on 2011-09-13
You never really state what you think is a problem.

Everything that you mentioned seems quite normal.

When the CPU "goes to 3.3GHz briefly when nothing is being done", how do you know nothing is being done? More likely something is being done (briefly).

I've noticed that people are often trying to outguess the OS (with memory usage, CPU usage, etc.), but Linux usually knows what it's supposed to do.

---

### Post by A Traveller on 2011-09-14
Thanks for your replies zero2xiii/Slim Odds.

'You never really state what you think is a problem.'

The problem is that I looked on the Internet to check if my CPU figures were normal but I came across a mixture of answers (normal and not normal) so I wanted to find out for certain. 

So it is normal that all only one of the cores goes to 3.3GHz (different ones at different times)?

If I quickly learn how to edit/render video, what should I see for each core if I run cat /proc/cpuinfo?

At the moment this is what I get if I play an hd video on youtube (on this occasion it's processor 4 that shows 3300.000:-

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 10
model name	: AMD Phenom(tm) II X6 1100T Processor
stepping	: 0
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 6
core id		: 0
cpu cores	: 6
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpb npt lbrv svm_lock nrip_save pausefilter
bogomips	: 6629.37
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate [9]

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 10
model name	: AMD Phenom(tm) II X6 1100T Processor
stepping	: 0
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 6
core id		: 1
cpu cores	: 6
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpb npt lbrv svm_lock nrip_save pausefilter
bogomips	: 6629.31
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate [9]

processor	: 2
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 10
model name	: AMD Phenom(tm) II X6 1100T Processor
stepping	: 0
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 6
core id		: 4
cpu cores	: 6
apicid		: 2
initial apicid	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpb npt lbrv svm_lock nrip_save pausefilter
bogomips	: 6629.32
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate [9]

processor	: 3
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 10
model name	: AMD Phenom(tm) II X6 1100T Processor
stepping	: 0
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 6
core id		: 2
cpu cores	: 6
apicid		: 3
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpb npt lbrv svm_lock nrip_save pausefilter
bogomips	: 6629.32
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate [9]

processor	: 4
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 10
model name	: AMD Phenom(tm) II X6 1100T Processor
stepping	: 0
cpu MHz		: 3300.000
cache size	: 512 KB
physical id	: 0
siblings	: 6
core id		: 5
cpu cores	: 6
apicid		: 4
initial apicid	: 5
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpb npt lbrv svm_lock nrip_save pausefilter
bogomips	: 6629.32
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate [9]

processor	: 5
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 10
model name	: AMD Phenom(tm) II X6 1100T Processor
stepping	: 0
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 6
core id		: 3
cpu cores	: 6
apicid		: 5
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpb npt lbrv svm_lock nrip_save pausefilter
bogomips	: 6629.30
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate [9]

---

### Post by Slim Odds on 2011-09-14
There is no reason that you would want all the cores switching to 3.3GHz at the same time, since most are idle. That would be a big power waster.

Also, I don't think that youtube is running multi-threaded (flash). So one core is likely all that it is using. Maybe someone else knows more about that.

---

### Post by pqwoerituytrueiwoq on 2011-09-14
add the system monitor to your panel and watch the cpu usage
odds are it is bumping up that high to compensate for the gpu
if you you are trying to make it more "green" set it to conservative
just edit line 27 of /etc/init.d/ondemand
only one cores jumps with flash as it is a single thread program

cool -n- quite is just a 'green mode'
the 3.3ghz is the stock speed running in performance mode is not over-clocking it is just a bit wasteful in power for idle if yuo are worried about temperature just ensure there is proper ventilation (made a side airduct and lowered my cpu temp ~10C)

to lower cpu usage for youtube flash videos pause the video and run this command
```
d="`date`";ln -s `f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"` /tmp/"movie-$d";totem /tmp/"movie-$d"
```
that also works with megavideo/videozer/myspace/facebook streaming content

---

### Post by Mark Phelps on 2011-09-14
Something to think about ...

I have the very same motherboard but with an AMD 1090T.

The board came with BIOS version FF.  With that, I was able to run 1600 memory full speed without problems.  I was also able to monitor the usage of all six of the cores using GKRellM, again, with no problem.

Then, I upgraded the BIOS version to FGA.  After that, I had to step back the memory to 1333.  The board would not boot with the memory set any faster.

Then recently, I upgraded the BIOS again to FGF -- this is the version that claims to have support for the AM3+ processors.

After that, I could not run the system memory faster than 1066.

As a test, I restore the orignal FF BIOS -- and made no other changes.  NOW, I am once again able to run the memory at 1600.

So, there may be something wrong with the FGF BIOS.  Suggest that you check on the Gigabyte forums to get more info.

---

### Post by A Traveller on 2011-09-15
Ok thanks Slim Odds.

Hi pqwoerituytrueiwoq. It must be a pain for you when filling out application forms with a name like that! Haha. Thanks for your reply.

Hi Mark Phelps. It's a coincidence that just before I saw your post, I had read the following post on the Gigabyte forums:-

[http://forum.giga-byte.co.uk/index.php/topic,6682.0.html](http://forum.giga-byte.co.uk/index.php/topic,6682.0.html)

Thanks for your advice.

---

### Post by A Traveller on 2011-09-15
Hi all. Here is what I get when I disable Cool and Quiet:-

Thanks for all the help and advice everyone.

processor : 0
vendor_id : AuthenticAMD
cpu family : 16
model : 10
model name : AMD Phenom(tm) II X6 1100T Processor
stepping : 0
cpu MHz : 3314.698
cache size : 512 KB
physical id : 0
siblings : 6
core id : 0
cpu cores : 6
apicid : 0
initial apicid : 0
fpu : yes
fpu_exception : yes
cpuid level : 6
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpb npt lbrv svm_lock nrip_save pausefilter
bogomips : 6629.39
TLB size : 1024 4K pages
clflush size : 64
cache_alignment : 64
address sizes : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate [9]

processor : 1
vendor_id : AuthenticAMD
cpu family : 16
model : 10
model name : AMD Phenom(tm) II X6 1100T Processor
stepping : 0
cpu MHz : 3314.698
cache size : 512 KB
physical id : 0
siblings : 6
core id : 1
cpu cores : 6
apicid : 1
initial apicid : 1
fpu : yes
fpu_exception : yes
cpuid level : 6
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpb npt lbrv svm_lock nrip_save pausefilter
bogomips : 6629.31
TLB size : 1024 4K pages
clflush size : 64
cache_alignment : 64
address sizes : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate [9]

processor : 2
vendor_id : AuthenticAMD
cpu family : 16
model : 10
model name : AMD Phenom(tm) II X6 1100T Processor
stepping : 0
cpu MHz : 3314.698
cache size : 512 KB
physical id : 0
siblings : 6
core id : 5
cpu cores : 6
apicid : 2
initial apicid : 5
fpu : yes
fpu_exception : yes
cpuid level : 6
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpb npt lbrv svm_lock nrip_save pausefilter
bogomips : 6629.31
TLB size : 1024 4K pages
clflush size : 64
cache_alignment : 64
address sizes : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate [9]

processor : 3
vendor_id : AuthenticAMD
cpu family : 16
model : 10
model name : AMD Phenom(tm) II X6 1100T Processor
stepping : 0
cpu MHz : 3314.698
cache size : 512 KB
physical id : 0
siblings : 6
core id : 2
cpu cores : 6
apicid : 3
initial apicid : 2
fpu : yes
fpu_exception : yes
cpuid level : 6
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpb npt lbrv svm_lock nrip_save pausefilter
bogomips : 6629.31
TLB size : 1024 4K pages
clflush size : 64
cache_alignment : 64
address sizes : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate [9]

processor : 4
vendor_id : AuthenticAMD
cpu family : 16
model : 10
model name : AMD Phenom(tm) II X6 1100T Processor
stepping : 0
cpu MHz : 3314.698
cache size : 512 KB
physical id : 0
siblings : 6
core id : 4
cpu cores : 6
apicid : 4
initial apicid : 4
fpu : yes
fpu_exception : yes
cpuid level : 6
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpb npt lbrv svm_lock nrip_save pausefilter
bogomips : 6629.31
TLB size : 1024 4K pages
clflush size : 64
cache_alignment : 64
address sizes : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate [9]

processor : 5
vendor_id : AuthenticAMD
cpu family : 16
model : 10
model name : AMD Phenom(tm) II X6 1100T Processor
stepping : 0
cpu MHz : 3314.698
cache size : 512 KB
physical id : 0
siblings : 6
core id : 3
cpu cores : 6
apicid : 5
initial apicid : 3
fpu : yes
fpu_exception : yes
cpuid level : 6
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpb npt lbrv svm_lock nrip_save pausefilter
bogomips : 6629.31
TLB size : 1024 4K pages
clflush size : 64
cache_alignment : 64
address sizes : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate [9]

---

### Post by Ceiber Boy on 2011-09-15
The usage of the CPU varies on the construct of the program. A few things to consider when looking at CPU usage when a program in running is the programs multi-threading, multi-core and multi-processor capabilities.

For example when I open LARGE PDF documents in Document Viewer all four of my processors will max out. but when I render video only one of the cores will max out.

So in short, It just depends on what resources the program has told to take advantage of. So without an interment knowledge of each and every program running on your maching it really is difficult to say why the CPU level is what it is.

The only thing I would say with Linux (whether this is correct or not I would not like to say but this is just my observation) is that it seams to be more power hungry than windows, however I left windows behind along time ago with XP being my last windows OS, and things have moved on considerably since then.

---

### Post by A Traveller on 2011-09-15
Thanks for that info Ceiber Boy. I think everything is working fine and as it should.

---

