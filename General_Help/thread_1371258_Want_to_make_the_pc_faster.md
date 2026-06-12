---
title: "Want to make the pc faster"
date: 2010-01-03
forum: General Help
---

### Post by Deldo on 2010-01-03
Hi.

I noticed that my computer is slow. Very slow. I don't know what I have done, but I would like to hear if there is any program or anything that can solve the problem for me?

Rune

---

### Post by s.fox on 2010-01-03
Hi,

Can you please list your hardware specifications?

I would also look [here]("http://ubuntuforums.org/showthread.php?t=652792") for some suggestions :)

-Silver Fox

---

### Post by MelDJ on 2010-01-03
try a lighter de like lxde

---

### Post by cascade9 on 2010-01-03
> **Deldo said:**
> Hi.

I noticed that my computer is slow. Very slow. I don't know what I have done, but I would like to hear if there is any program or anything that can solve the problem for me?

Rune

Was it faster before? If it was, its possible that something has gone wrong. 

If not, then you might need to do some stuff to make it faster. I'd try a minimal install, MelDJs suggestion of a light DE.

---

### Post by 3rdalbum on 2010-01-03
If your computer is running slowly, then the easiest explanation is that a runaway program is using a lot of your CPU power.

What does the System Monitor say about your CPU use (as in how much is being used)? If your CPU use is sitting at or close to 100% you need to check the "Processes" list to see what program is using it all (hint: Click the "% CPU" column to sort the list by amount of CPU used).

When you find out what program is using all your CPU power, then kill it and see what happens.

---

### Post by Deldo on 2010-01-03
I have a ASUS X72Vn
Intel Duo P7350
4 GB Ram

I don't have anything major running that requiers that much power.
Even when I'm typing here, some of the words are written after I typed them.
Rhythmbox stops playing for under a second when I scroll down a page in Firefox, for example.

---

### Post by mkvnmtr on 2010-01-03
My machines begin acting funny when the hard drive gets to about 90% full. It is something to check. I believe I remember on 6.10 or 7.04 I had a runaway log file thet filled my hard drive.

---

### Post by Deldo on 2010-01-03
I haven't even used 1% of my hard drive (1 TB). I have a external hard drive which all my files are on, in case that my computer crashes.

---

### Post by rantingkitten on 2010-01-03
One thing I've noticed is that Ubuntu (and many other Linux distros) tend to use the lowest possible processor speed.  It's not widely known but most processors can step up or throttle back their speed to conserve power, and for some reason, Linux tends to default to the lowest speed.  In theory it will crank up the speed when needed, but it's not always great at doing this.

You can find out your processor speed by typing:

cat /proc/cpuinfo

You'll get a bunch of information for all your processors, and in there you'll see a line that says "cpu MHz".  If yours is abnormally low, there's a problem.

You can usually fix this by installing cpufreqd, which is a daemon that controls processor frequency.  

apt-get install cpufreqd

Once installed, check your speed again.  Chances are it will be at the maximum for your particular processor.  If not, you can read up on how to use cpufreq to manipulate the speed.

If this isn't helpful, you can also use the command 'top' to see what's eating your processor cycles and memory.

Good luck.

---

### Post by Deldo on 2010-01-03
Is 800.000 Mhz low?
I now followed your guide and installed cpufreqd. The "cpu Mhz" (by the command cat /proc/cpuinfo) is now set to 2000.000 Mhz in both CPU's. I will tjeck if my machine i faster.

---

### Post by dnr1128 on 2010-01-03
I ran the cpuinfo, and it showed my processor speed to be 600mhz on my processor which is 1.73ghz.  After installing cpufreqd it now shows the speed to be 1ghz.  how to I adjust the other settings?

---

### Post by dnr1128 on 2010-01-03
SOLVED

when i last checked, I was running on battery power.  I went back on ac power and checked it again and its showing at full speed.

---

### Post by turboopugsleylx on 2010-01-04
I checked mine...I have a AMD Athlon x2 and it is a 2700Mhz but when I ran that it said my processor was running at 1300Mhz....since mine is a dual core is this normal or does this mean my processor is running at half speed?

---

### Post by rantingkitten on 2010-01-04
If you have a dual core system you'll just see two sets of cpu information, one for each core.  They do not run at half speed or anything like that, so no, that is not normal.  First, are you plugged into the AC power when you do this?  Some laptops will throttle back on battery power.  If you're plugged in, or this isn't a laptop, then you ran into the problem I mentioned, so you should get cpufreqd.

---

### Post by ssulaco on 2010-01-04
> **rantingkitten said:**
> 

You can find out your processor speed by typing:

cat /proc/cpuinfo


I like that command,**Thankyou**....did not know that my processor might not be fully utilized.

---

### Post by rantingkitten on 2010-01-05
Yup, no problem.  

I do want to add that if you're doing this on a laptop your battery life will be reduced a bit -- probably not much -- because the processor is always running at full speed.  

As I mentioned, the idea behind the ability to throttle the speed is that it can always crank up the speed if you're doing something processor-intensive, and then crank it back down when the computer isn't doing much, so as to save power.  

The problem is, it's not always good at doing this, and sometimes it doesn't work at all.  

Now, personally, I don't mind the processor running at full speed all the time.  I still manage to get about 2.5 hours of battery life out of mine.  But different hardware and different batteries will give different results, so some of you might care about this sort of thing.

The way to test is to run 'cat /proc/cpuinfo' when the computer is just sitting there, and see what the reported speed is.

Then, do something that takes some serious processor power.  Run like five videos on youtube, or run some echo effects on an mp3 in audacity, or compile something, I don't know.  Be creative.  Anyway, while that's running, check your cpu speed again.

If it goes up, you're probably safe -- your cpu speed is increasing on demand and going back down when there's no demand.  If it stays the same, that's when you know there's a problem. 

[andy zebrowitz]("http://mirrorshades.org/wc")

---

### Post by turboopugsleylx on 2010-01-05
Heres what its showing me

processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Athlon(tm) 7750 Dual-Core Processor
stepping    : 3
cpu MHz        : 1350.000
cache size    : 512 KB
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5425.48
clflush size    : 64
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Athlon(tm) 7750 Dual-Core Processor
stepping    : 3
cpu MHz        : 1350.000
cache size    : 512 KB
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5424.73
clflush size    : 64
power management: ts ttp tm stc 100mhzsteps hwpstate

---

### Post by turboopugsleylx on 2010-01-06
Anyone?

---

### Post by head2head on 2010-01-06
In my install of Karmic, I've got my cpu (a quad core athlon) set to run at speeds relevant to what I'm using at the time. i.e. when I'm doing intensive things like encoding, it will shoot up to using full power (2.6 ghz), but most of the time its running at 800mhz. 

It could be yours is doing the same thing. There's something you can add to the panel to monitor your cpu speed...its called 'cpu freqency monitor'. Add that to the panel and see if the speed changes.

If I remember correctly, you should be able to set it to run at a set speed all the time, or optimise it according to load.

Hope that helps!

---

### Post by bobcollard on 2010-01-06
> **Deldo said:**
> Hi.

I noticed that my computer is slow. Very slow. I don't know what I have done, but I would like to hear if there is any program or anything that can solve the problem for me?

Rune
How fast is your external drive with all your programs on it?  Is it USB 1 or 2?  Firewire?  Networked?   How much RAM do you have and how often do you restart your computer?  All of these things slow it down.  Try Xubuntu, it's faster than Ubuntu and Kubuntu.

---

### Post by Deldo on 2010-01-07
"cpufreqd" did the job. It proberly didn't work so well switching to high and low power.

---

### Post by turboopugsleylx on 2010-01-07
Yeh the CPU Freq worked for me as well...question is I installed the software the edit and adjust the cpu...but I cant find out how to get into it at all...any help?

---

### Post by sarin_cv on 2010-01-07
I also installed it... but now, how can I disable it?

---

### Post by turboopugsleylx on 2010-01-08
Id like to know how to disable/adjust it....anyone?

---

### Post by turboopugsleylx on 2010-01-08
anyone? or does anyone know a software that can allow me to adjust this stuff without having to type into anything thru a terminal (more like a windows program)?

---

### Post by wojox on 2010-01-12
Right click the panel and add to CPU Frequency Scaling Monitor.

---

### Post by Trizzy on 2010-01-14
Wow. I didn't even realize my cpu was running slower than it was rated for. 800 Mhz is now 1800 Mhz. Thanks!

---

