---
title: "swapiness &amp; swap file"
date: 2010-02-15
forum: General Help
---

### Post by KegHead on 2010-02-15
Hi!

My swap file is 5.8 gb and I have a swappiness of 60.

Is there any reason to increase any of these values?

Thanks!

KegHead

---

### Post by audiomick on 2010-02-15
Probably not. If you have a "modern" amount of RAM, i.e upwards of 1GB, you are likely to not even get near the swap space, unless you are doing something (large scale video editing, for instance) that is really RAM intensive.

---

### Post by KegHead on 2010-02-15
Hi!

2gb ram.

KegHead

---

### Post by audiomick on 2010-02-15
Yes, as I said, "normal" use will probably never even scratch your swap space. You can watch it using
system> adminstration> system monitor
bearing in mind that it uses a bit of RAM for itself, or in a terminal with
```
top
```
which, I think, will show you slightly different numbers than the system monitor.
If you watch top for a while, you will notice the cache growing. This is normal and ok, and does not mean that this RAM is no longer available for programs. Ubuntu accumulates cache space as it runs, but gives it up immediately if a program needs it.

One reason I have read of for reducing swappiness is to try and gain a bit of speed. I have never felt the need, and I think that on a halfway modern system there is generally no need for it.

---

### Post by KegHead on 2010-02-15
Thanks, this is where I'm at:
jim@jim-desktop:~$ top

top - 12:11:55 up 48 min,  2 users,  load average: 0.00, 0.01, 0.03
Tasks: 194 total,   2 running, 192 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.8%us,  0.6%sy,  0.0%ni, 98.4%id,  0.2%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2051852k total,  1580924k used,   470928k free,    21756k buffers
Swap:  6008268k total,        0k used,  6008268k free,   737404k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1039 root      20   0 58584  16m 7744 R    2  0.8   1:26.83 Xorg               
21293 jim       20   0 38104  12m 9544 S    1  0.6   0:00.93 gnome-terminal     
 2744 jim       20   0 68788  23m 7756 S    1  1.2   0:24.12 compiz.real        
10783 jim       20   0  128m  15m  12m S    1  0.8   0:19.76 chrome             
21399 jim       20   0  2472 1208  884 R    1  0.1   0:00.14 top                
 7458 jim       20   0  151m  70m  14m S    0  3.5   1:43.37 chrome             
    1 root      20   0  2532 1524 1128 S    0  0.1   0:01.58 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.01 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.01 ksoftirqd/2        
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2         

KegHead

---

### Post by oldos2er on 2010-02-15
> **KegHead said:**
> My swap file is 5.8 gb and I have a swappiness of 60.

Is there any reason to increase any of these values?


 No, but in my opinion, there are reasons to decrease them. Does your system ever become heavily loaded enough to use swap? Do you use hibernation?

---

### Post by KegHead on 2010-02-15
Hi!

No, I use this self made computer for internet, WP and spreadsheets.

It's quite speedy for a budget Atom 330 build, I was hoping to squeeze out every once of performance.

KegHead

---

### Post by audiomick on 2010-02-15
Your top is showing usage of about 1.5 GB of RAM, and it has about 749MB cached. If that is taken during "normal" use, you could conceivably reduce the size of your swap partition. If you are not short of drive space, though, you could leave it until you do a fresh install in the future.

---

### Post by KegHead on 2010-02-15
Hi!

I have tons of drive space left.

I'll leave alone 'til next version, 10.4!

KegHead

---

### Post by audiomick on 2010-02-15
I just remembered this:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by KegHead on 2010-02-15
Hi!

I read this article.

Thanks.

KegHead

---

### Post by oldos2er on 2010-02-15
I usually set swappiness to 5, with a 1GB swap file. Since I never use hibernation, the system never swapped (this was when I had 2GB RAM).

---

### Post by KegHead on 2010-02-15
Hi!

Why so low?

Swappiness is set at 60 during installation and the swap file was done automatically.

KegHead

---

### Post by 2hot6ft2 on 2010-02-15
I set swappiness to 10 that way it will use 90% of the RAM before it starts using swap since RAM is faster than swap.

---

### Post by KegHead on 2010-02-15
Hi!

Wow that makes sense.

I'll try it!

KegHead

---

### Post by uRock on 2010-02-15
I have 2 gigs RAM and a 7.5 gig Swap partition. I have filled them both to 98 percent running Wireshark while major files were being transfered.

---

### Post by 2hot6ft2 on 2010-02-15
> **KegHead said:**
> Hi!

Wow that makes sense.

I'll try it!

KegHead
I'm sure you'll like it. That's what I do with every install. It's one of the best and easiest mods there is.

---

### Post by oldos2er on 2010-02-16
> **KegHead said:**
> Why so low?

Because I don't want the system to use swap unless absolutely necessary.

---

### Post by NightwishFan on 2010-02-16
I always set my swappiness to 100 because my system tends to need to swap anyway at 895mb RAM.

---

### Post by KegHead on 2010-02-16
Hi!

There are a lot of conflicting views.

My Dell mini 9 seems faster and my self-build Atom 330 also.

Swappiness set at 10 for both.

Both have 2gb ram, Dell w/16gb ssd, Self made-160 gb.

KegHead

---

### Post by KegHead on 2010-02-18
Hi!

The swappiness at 10 has helped1

I also set compiz up to the max!

KegHead

---

### Post by mcduck on 2010-02-18
> **2hot6ft2 said:**
> I set swappiness to 10 that way it will use 90% of the RAM before it starts using swap since RAM is faster than swap.

That is not true in any way.

Swappiness isn't any direct percentage value of RAM to use before using the swap. It's one of the values the kernel uses when dtermining wether to swap something or not, and the actual process is a bit more complicated than that.

The actual swap usage, *swap_tendency* is then calculated like this:
*swap_tendency* = *mapped_ratio*/2 + *distress* + *vm_swappiness*
[I]
distress[/I] is a value telling how much troubles kernel is having freeing memory. it starts from zero and grows up to 100 based on how many attempts the kernel needs to do until it's able to allocate memory for something.
[I]
mapped_ratio[/I] is approximate percentage of how much of the system's total memory is mapped.
[I]
vm_swappiness[/I] is a parameter used to configure how much kernel should prefer swapping versus dropping cached data.

So, even with swappiness set to 0 the kernel will use swap if it needs to, and even with swappiness set to 100 the kernel doesn't always use swap.

(since swapping isn't something you'd actually *want* to do unless there are no other options, you don't usually want to increase the swappiness value from defaults. And if you have enough RAM that the swap isn't used, lowering the swappiness value will have *absolutely no effect* on your system's performance.)

---

### Post by 2hot6ft2 on 2010-02-18
> **mcduck said:**
> That is not true in any way.
I've always understood that RAM is faster that swap. So that's NOT true? Not being sarcastic, it's a question. I just re-read it and it doesn't sound quite right.

> **mcduck said:**
> 
vm_swappiness[/I] is a parameter used to configure how much kernel should prefer swapping versus dropping cached data.

So, even with swappiness set to 0 the kernel will use swap if it needs to, and even with swappiness set to 100 the kernel doesn't always use swap.

(since swapping isn't something you'd actually *want* to do unless there are no other options, you don't usually want to increase the swappiness value from defaults. And if you have enough RAM that the swap isn't used, lowering the swappiness value will have *absolutely no effect* on your system's performance.)
Then does it do anything?
Or is it an irrelevant value?

I mean if you're making it "prefer swapping" less then it should have exactly that effect.
Which would in turn mean it would use RAM more.
Sure it will still use swap when it needs to.

---

### Post by mcduck on 2010-02-18
> **2hot6ft2 said:**
> Then does it do anything?
Or is it an irrelevant value?

I mean if you're making it "prefer swapping" less then it should have exactly that effect.
Which would in turn mean it would use RAM more.
Sure it will still use swap when it needs to.

yes, it does do something. It allows for some level of fine-tuning of the system's tendency to swap versus keeping _cached data_ in RAM.

The important point is that it's not a direct control over the swap usage. And the system will always use as much RAM as it can. Adjusting swappiness won't effect that in any way.

The only sensible situation to change the swappiness value I can even think of is a laptop with fairly little of RAM (so that the system actually needs to swap occassionally) and log files turned off, and being used mostly for web surfing or other tasks where most of the used data comes from somewhere else than your hard drive. In that situation setting a low swappiness value *might* allow the laptop's hard drive to sleep a bit more, giving you a slight increase in battery life (at the expense of performance, extremely so when doing anyhting that actually *uses* data from the hard drive).

---

### Post by uRock on 2010-02-18
Where or how does one adjust the swappiness?

---

### Post by KegHead on 2010-02-18
Hi!

So, if I understand correctly-the 60 setting is optimal with a decent desktop system w/2 gb ram and 160 gb hd?

Thanks for all of your help!

KegHead

---

### Post by 2hot6ft2 on 2010-02-18
> **mcduck said:**
> yes, it does do something. It allows for some level of fine-tuning of the system's tendency to swap versus keeping _cached data_ in RAM.

The important point is that it's not a direct control over the swap usage. And the system will always use as much RAM as it can. Adjusting swappiness won't effect that in any way.

The only sensible situation to change the swappiness value I can even think of is a laptop with fairly little of RAM (so that the system actually needs to swap occassionally) and log files turned off, and being used mostly for web surfing or other tasks where most of the used data comes from somewhere else than your hard drive. In that situation setting a low swappiness value *might* allow the laptop's hard drive to sleep a bit more, giving you a slight increase in battery life (at the expense of performance, extremely so when doing anyhting that actually *uses* data from the hard drive).
Thanks for the clarification. I stand corrected then.

---

### Post by doas777 on 2010-02-18
> **KegHead said:**
> Hi!

So, if I understand correctly-the 60 setting is optimal with a decent desktop system w/2 gb ram and 160 gb hd?

Thanks for all of your help!

KegHead


basically. you always need at least teh amount of ram you have in swap space if you wanna hibernate/suspend, so 1.5x Ram is a good setting.

---

### Post by KegHead on 2010-02-18
Hi!

Wow!

I guess this is what Ubuntu is all about, serious friendly help!

KegHead

---

### Post by mcduck on 2010-02-18
> **KegHead said:**
> Hi!

So, if I understand correctly-the 60 setting is optimal with a decent desktop system w/2 gb ram and 160 gb hd?

Thanks for all of your help!

KegHead

With 2GB of RAM it's unlikely that your system would ever really even use the swap (apart from storing the contents of your RAM if you hibernate the machine), so swappiness value will have absolutely no effect regardless of what you set it to. You can happily leave it to the default setting. :)

---

### Post by KegHead on 2010-02-18
copy.

---

### Post by wojox on 2010-02-18
> **iRock said:**
> Where or how does one adjust the swappiness?

[http://wojox.homelinux.net/?p=49](http://wojox.homelinux.net/?p=49)

---

### Post by 2hot6ft2 on 2010-02-18
> **KegHead said:**
> Hi!

Wow!

I guess this is what Ubuntu is all about, serious friendly help!

KegHead
That's what it's all about. We're here to learn, and to help others learn. To share our knowledge, and to acquire the knowledge of those who know more than ourselves.
Welcome aboard.
:popcorn:

---

### Post by dcstar on 2010-02-18
> **doas777 said:**
> basically. you always need at least teh amount of ram you have in swap space if you wanna hibernate/suspend, so 1.5x Ram is a good setting.

Rubbish, there is no "N.N x RAM" setting that is good or bad. You need as much Swap space as YOUR system needs - no more and no less.

If you are going to use hibernation then you need Swap to be at least your physical RAM size (because Hibernation copies a "snapshot" of the RAM contents into that filespace and then copies it back into RAM when you come out of hibernation) but no more.

If you have plenty of RAM for the apps you run and do not use hibernation then you may need little or no Swap - it all depends on how much disk space you want to use (waste) on it.

Disregard any "Rule of thumb" statements you ever see saying things like "You should have 2X RAM for you swap" because these now are basically just parroted myths that originated from a time long ago when physical RAM was an expensive commodity and systems invariably ran with most of their active processes in swap - this is rarely the case now.

Have as much swap as you system actually needs, and if you have a reasonable amount of RAM don't bother wasting your time trying to manage swap better than the kernel - it also invariably knows better than you on how to do this job.

---

