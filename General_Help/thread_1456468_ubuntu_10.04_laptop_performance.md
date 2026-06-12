---
title: "ubuntu 10.04 laptop performance"
date: 2010-04-17
forum: General Help
---

### Post by Gorlist on 2010-04-17
Im not terribly sure where to post this, can't seem to find the 10.04 dev forums so I do apologise!

I decided to the take the plunge with my laptop and shift over to 10.04 before the official release. Partly due to im going on Holiday May the 2nd and need todo a reinstall, so thought I would test it before hand rather than just reinstalling 9.10. 

Something ive noticed is poor performance, is this down the fact its a pre-release and not fully optimised? or have the overheads increased?

Ive got a Athlon 64x2 Mobile 1.7Ghz with a ATI Xpress 1250, and have moved from the 32bit 9.10 to 64bit 10.04 (under the assumption it should run quicker). The general desktop feels sluggish, slow responding and applications take time to open and close, with allot of general pondering and rumbling. Compiz is already disabled.

Any ideas?

Best regards,

---

### Post by linden940 on 2010-04-17
64bit computers need MORE ram than a 32bit computer...if your computer has less than 4GB of ram...it will run slow...you should go back to 32bit if under 4GB of ram

---

### Post by howefield on 2010-04-17
You're right, the Lucid forum is a little hidden away.

[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

For me, the 10.04 overheads have reduced from 9.10 (also running 64 bit).

Memory will not be an issue unless you have very little, eg, 512 megs or less.

---

### Post by howefield on 2010-04-17
> **linden940 said:**
> ...if your computer has less than 4GB of ram...it will run slow...you should go back to 32bit if under 4GB of ram

Can you quantify that, how slow and why ?

64 bit runs perfectly well on much less than 4 gig.

---

### Post by linden940 on 2010-04-17
> **howefield said:**
> 
Memory will not be an issue unless you have very little, eg, 512 megs or less.

you think 10.04 64bit will/can run on only 512megs of ram???

---

### Post by howefield on 2010-04-17
> **linden940 said:**
> you think 10.04 64bit will/can run on only 512megs of ram???

Of course.

More is better, absolutely. But to say 64 bit will run slower than 32 bit unless you have 4 gig of RAM or more is simply untrue.

you think 10.04 64bit will/can run on more than 4 gigs of ram???

---

### Post by linden940 on 2010-04-17
> **howefield said:**
> Can you quantify that, how slow and why ?

64 bit runs perfectly well on much less than 4 gig.

64bit can run on less than 4gb of ram...but if you go to use programs that have a high ram usage it will slow you down....so *i did not set the line.....but Hp, dell and ect have* if its under 4gb of ram its a 32bit system...if its over 4gb of ram its 64bit of ram

and a 64bit of ram system is like a old car trying to win a race...it CAN race just fine...dont mean it will win tho.....but did he tell you WHAT he is doing that will cause his computer to RUN slow? for all we know..he is doing video editing on a 64bit system that has 1GB of ram or something like that

---

### Post by linden940 on 2010-04-17
this is MY opinion that a computer that runs a 64bit OS with less than (around 2.5GB or ram or so...is a very bad idea...)

4GB of ram on a 64bit system runs very well

but this thread is getting alittle off topic and we all have our own opinions.

---

### Post by Gorlist on 2010-04-17
thanks, right only running 1 gig of DDR shared with the graphics card. I might try 32bit sometime later in the week on the off chance.

And to answer linden940 just normal Firefox, Thunderbird and file browsing (nothing exciting!).

---

### Post by howefield on 2010-04-17
> **Gorlist said:**
> thanks, right only running 1 gig of DDR shared with the graphics card. I might try 32bit sometime later in the week on the off chance.

And to answer linden940 just normal Firefox, Thunderbird and file browsing (nothing exciting!).

Your issue is unlikely to be down to you using the 64 bit version. Are there any hardware drivers available for your graphics card ?

---

### Post by Gorlist on 2010-04-17
afraid not, only the opensource since 8.04 :(

---

### Post by 3rdalbum on 2010-04-17
64-bit means that certain mathematical operations run quicker (the ones that use 64-bit numbers). In general desktop use, you'll use so few 64-bit numbers that you won't notice a difference; plus of course a 64-bit operating system will not make your disk any faster.

Also, my father uses 64-bit Ubuntu with 1.25 GiB of RAM, some of that shared with the graphics card.

There must be a process that is using your CPU time or your computer's I/O capacity. You can use the "top" command to find out a heavy CPU-bound process and kill it. You can install the "iotop" package to find out the same thing with I/O.

---

### Post by Gorlist on 2010-04-17
> **3rdalbum said:**
> 64-bit means that certain mathematical operations run quicker (the ones that use 64-bit numbers). In general desktop use, you'll use so few 64-bit numbers that you won't notice a difference; plus of course a 64-bit operating system will not make your disk any faster.

Also, my father uses 64-bit Ubuntu with 1.25 GiB of RAM, some of that shared with the graphics card.

There must be a process that is using your CPU time or your computer's I/O capacity. You can use the "top" command to find out a heavy CPU-bound process and kill it. You can install the "iotop" package to find out the same thing with I/O.

Right, okay ive taken a look using top, and apart from xorg (15%) and Firefox-bin (22%) their doesn't appear to be any other real usage. So perhaps its more the graphics card/opensource related - either way it does feel sluggish/responsive compared to 9.10, but perhaps when we get closer to the 29th it will improve, if not will try the 32bit on the off chance.

On my main desktop system its fine.

Sorry I know its a bit of a vague topic. 

thanks.

---

### Post by philinux on 2010-04-17
@Gorlist: Post back what this says.

```
free -m
```

I'm running 64 bit with 2gig of ram on a desktop with a 512 meg ram nvidia card and it flies. Also not using mem to bad either. It could be the shared video memory or the graphics driver causing the problem. Lucid for me boots up in 21 seconds. From GDM to Desktop only takes 4 seconds.

```
free -m
             total       used       free     shared    buffers     cached
Mem:          2009        904       1105          0         87        335
-/+ buffers/cache:        **[COLOR="Red"]480 [/COLOR]**      1528
Swap:         1906          0       1906
```

---

### Post by Gorlist on 2010-04-17
```
james@james-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           744        718         25          0         24        269
-/+ buffers/cache:        424        319
Swap:         2178         34       2144

```

Their you go, so if I read that correctly ive only got 25 meg free memory?

---

### Post by howefield on 2010-04-17
> **Gorlist said:**
> so if I read that correctly ive only got 25 meg free memory?

No, it's the second line you want to read, you have 319 megs free and you are barely using swap.

---

### Post by almivlod on 2010-05-15
> **linden940 said:**
> you think 10.04 64bit will/can run on only 512megs of ram???

my config : msi er710 laptop, turion x2 1,6GHz with 2GB ram and ati 1270. Ubuntu 10.04 64 bit uses with running files Firefox & System monitor 446 Mb of ram. 1270 uses 256 MB from it.

Ubuntu recommended min. ram is 512 MB.

---

